---
title: F# を使用した Azure Queue Storage の概要
description: Azure キューは、アプリケーションコンポーネント間の信頼性の高い非同期メッセージングを提供します。 クラウドメッセージングを使用すると、アプリケーションコンポーネントを個別にスケーリングできます。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 65af98fb88e91d709eb0e35907cbc2dc097634d0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630487"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F を使用して Azure Queue storage の使用を開始する\#

Azure Queue storage は、アプリケーションコンポーネント間のクラウドメッセージングを提供します。 大規模なアプリケーションの設計では、多くの場合、アプリケーションコンポーネントが分離され、個別に拡張できるようになっています。 Queue storage は、アプリケーションコンポーネントがクラウド、デスクトップ、オンプレミスサーバー、モバイルデバイスのいずれで実行されているかにかかわらず、アプリケーションコンポーネント間の通信に使用する非同期メッセージングを提供します。 Queue storage では、非同期タスクの管理とプロセスワークフローの構築もサポートされています。

### <a name="about-this-tutorial"></a>このチュートリアルについて

このチュートリアルでは、Azure F# Queue storage を使用していくつかの一般的なタスクのコードを記述する方法について説明します。 キューの作成と削除、キューメッセージの追加、読み取り、削除などのタスクについて説明します。

Queue storage の概念の概要については、「 [.net のキューストレージに関するガイド](/azure/storage/storage-dotnet-how-to-use-queues)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するには、最初に[Azure ストレージアカウントを作成](/azure/storage/storage-create-storage-account)する必要があります。
また、このアカウントのストレージアクセスキーも必要になります。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成して、F# スクリプトと開始 F# 対話型

この記事のサンプルは、F# アプリケーションまたは F# スクリプトのいずれかで使用できます。 F# スクリプトを作成するには、ファイルを作成、`.fsx`拡張機能の例では、 `queues.fsx`、F# 開発環境にします。

次に、[パケット](https://fsprojects.github.io/Paket/)や`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)などの[パッケージマネージャー](package-management.md)を使用して、 `#r`ディレクティブを`WindowsAzure.Storage.dll`使用してスクリプトにパッケージと参照をインストールします。

### <a name="add-namespace-declarations"></a>名前空間宣言を追加する

ファイルの先頭`open`に次のステートメントを追加します。 `queues.fsx`

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>接続文字列を取得する

このチュートリアルでは、Azure Storage 接続文字列が必要です。 接続文字列の詳細については、「[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)」を参照してください。

このチュートリアルでは、次のように、スクリプトに接続文字列を入力します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

ただし、実際のプロジェクトではこの方法は**お勧めできません**。 ストレージアカウントキーは、ストレージアカウントのルートパスワードに似ています。 ストレージアカウントキーは常に慎重に保護してください。 他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーンテキストファイルに保存したりしないでください。 侵害された可能性があると思われる場合は、Azure ポータルを使用してキーを再生成することができます。

実際のアプリケーションでは、ストレージ接続文字列を維持する最善の方法は構成ファイルにあります。 構成ファイルから接続文字列を取得するには、次の手順を実行します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure Configuration Manager の使用は省略可能です。 .NET Framework の`ConfigurationManager`型などの API を使用することもできます。

### <a name="parse-the-connection-string"></a>接続文字列を解析する

接続文字列を解析するには、次のように指定します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

これにより、 `CloudStorageAccount`が返されます。

### <a name="create-the-queue-service-client"></a>Queue サービスクライアントを作成する

クラス`CloudQueueClient`を使用すると、Queue storage に格納されているキューを取得できます。 サービスクライアントを作成する方法の1つを次に示します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

これで、からデータを読み取り、キューストレージにデータを書き込むコードを記述する準備ができました。

## <a name="create-a-queue"></a>キューを作成する

この例では、キューが存在しない場合に作成する方法を示します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>メッセージをキューに挿入する

既存のキューにメッセージを挿入するには、最初に`CloudQueueMessage`新しいを作成します。 次に、 `AddMessage`メソッドを呼び出します。 は`CloudQueueMessage` 、次のように、文字列 (utf-8 形式) `byte`または配列のいずれかから作成できます。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>次のメッセージを見る

キューの先頭にあるメッセージをキューから削除せずにピークするには、 `PeekMessage`メソッドを呼び出します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>処理する次のメッセージを取得します。

キューの先頭にあるメッセージを取得するには、 `GetMessage`メソッドを呼び出します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

後でを使用`DeleteMessage`して、メッセージの処理が成功したことを示します。

## <a name="change-the-contents-of-a-queued-message"></a>キューに置かれたメッセージの内容を変更する

取得したメッセージの内容をキュー内のインプレースで変更できます。 メッセージが作業タスクを表している場合は、この機能を使用して作業タスクの状態を更新できます。 次のコードでは、キューメッセージを新しい内容で更新し、表示タイムアウトを別の60秒に拡張するように設定しています。 これにより、メッセージに関連付けられている作業の状態が保存され、メッセージの処理を続行するためにクライアントにもう1分の時間が与えられます。 この手法を使用すると、キューメッセージの複数ステップのワークフローを追跡できます。ハードウェアまたはソフトウェアの障害が原因で処理手順が失敗した場合、最初からやり直す必要はありません。 通常は、再試行回数も保持します。また、メッセージが何回も再試行される場合は、削除します。 これにより、処理されるたびにアプリケーションエラーをトリガーするメッセージから保護されます。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>次のメッセージをキューから解除する

コードでは、2つの手順でキューからメッセージをキューから除外します。 を呼び出す`GetMessage`と、キュー内の次のメッセージが取得されます。 から`GetMessage`返されたメッセージは、このキューからメッセージを読み取る他のコードからは見えなくなります。 既定では、このメッセージは30秒間非表示のままになります。 キューからのメッセージの削除を完了するには、も`DeleteMessage`を呼び出す必要があります。 メッセージを削除するこの2段階のプロセスでは、ハードウェアまたはソフトウェアの障害によってコードがメッセージの処理に失敗した場合に、コードの別のインスタンスが同じメッセージを取得して、もう一度試すことができます。 コードは、 `DeleteMessage`メッセージが処理された直後にを呼び出します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>一般的な Queue storage Api での非同期ワークフローの使用

この例では、一般的な Queue storage Api で非同期ワークフローを使用する方法を示します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>キューからメッセージを解除するための追加オプション

キューからのメッセージの取得をカスタマイズするには、2つの方法があります。
まず、メッセージのバッチを取得できます (最大 32)。 2つ目の方法として、非表示タイムアウトを長くまたは短くすることができます。これにより、コードで各メッセージを完全に処理できるようになります。 次のコード例で`GetMessages`は、を使用して1回の呼び出しで20個のメッセージを取得し、各メッセージを処理します。 また、各メッセージの非表示タイムアウトを5分に設定します。 5分がすべてのメッセージに対して同時に開始されるため、の呼び出し`GetMessages`から5分が経過すると、削除されていないメッセージは再び表示されることに注意してください。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>キューの長さを取得する

キュー内のメッセージ数の見積もりを取得できます。 メソッド`FetchAttributes`は、メッセージ数を含むキューの属性を取得するように Queue サービスに要求します。 プロパティ`ApproximateMessageCount`は、Queue サービスを呼び出さずに`FetchAttributes` 、メソッドによって取得された最後の値を返します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>キューを削除する

キューおよびキューに格納されているすべてのメッセージを削除`Delete`するには、キューオブジェクトに対してメソッドを呼び出します。

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>次の手順

これで、Queue storage の基本を学習できました。さらに複雑なストレージタスクの詳細については、次のリンク先を参照してください。

- [.NET 用 Api の Azure Storage](/dotnet/api/overview/azure/storage)
- [Azure Storage 型プロバイダー](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure Storage チームのブログ](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure Storage 接続文字列を構成する](/azure/storage/common/storage-configure-connection-string)
- [Azure Storage Services REST API リファレンス](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
