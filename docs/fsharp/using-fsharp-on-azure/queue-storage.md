---
title: F# を使用した Azure Queue Storage の概要
description: Azure キューでは、アプリケーション コンポーネント間で信頼性の高い非同期メッセージングを提供します。 クラウド メッセージングにより、アプリケーションのコンポーネントを個別にスケーリングします。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 58a46dfe905a32be77a13d11df8f0544546ea0ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756378"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F を使用した Azure Queue storage を概要します。\#

Azure Queue storage は、アプリケーション コンポーネント間のクラウド メッセージングを提供します。 スケールのアプリケーションを設計するには、アプリケーション コンポーネントは多くの場合、分離、それらを個別に拡張できるようにします。 キュー ストレージは、クラウド、デスクトップ、オンプレミス サーバーでは、またはモバイル デバイスで実行されているかどうか、アプリケーション コンポーネント間の通信用の非同期メッセージングを提供します。 Queue storage では、非同期タスクの管理とプロセス ワークフローの構築もサポートします。

### <a name="about-this-tutorial"></a>このチュートリアルについて

このチュートリアルは、記述する方法を示しています。 F# Azure Queue storage を使用して一般的なタスクのコード。 作成しキューの削除し追加、読み取り、およびキュー メッセージを削除する対象のタスクが含まれます。

Queue storage の概念的概要についてを参照してください[queue storage .NET ガイド](/azure/storage/storage-dotnet-how-to-use-queues)します。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成](/azure/storage/storage-create-storage-account)です。
このアカウントのストレージ アクセス キーも必要になります。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成して、F# スクリプトと開始 F# 対話型

この記事のサンプルは、F# アプリケーションまたは F# スクリプトのいずれかで使用できます。 F# スクリプトを作成するには、ファイルを作成、`.fsx`拡張機能の例では、 `queues.fsx`、F# 開発環境にします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケット](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブ。

### <a name="add-namespace-declarations"></a>名前空間宣言を追加します。

次の追加`open`ステートメントの先頭に、`queues.fsx`ファイル。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>接続文字列を取得します。

このチュートリアルでは、Azure Storage 接続文字列を必要があります。 接続文字列の詳細については、次を参照してください。[ストレージ接続文字列を構成](/azure/storage/storage-configure-connection-string)します。

チュートリアルでは、次のように、スクリプトで、接続文字列を入力します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

ただし、これは**しないで**の実際のプロジェクト。 ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存することは、他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure Portal を使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージ接続文字列を維持するために最善の方法は、構成ファイルです。 構成ファイルから接続文字列を取得するには、は、これを行うことができます。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure Configuration Manager の使用は省略可能です。 .NET Framework のなどの API を使用することもできます。`ConfigurationManager`型。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のように使用します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

これにより返されます、`CloudStorageAccount`します。

### <a name="create-the-queue-service-client"></a>Queue サービス クライアントを作成します。

`CloudQueueClient`クラスでは、Queue storage に格納されているキューを取得することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

キュー ストレージからデータを読み書きするコードを記述する準備が整いました。

## <a name="create-a-queue"></a>キューを作成します。

この例では、存在しない場合は、キューを作成する方法を示します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>キューにメッセージを挿入します。

既存のキューにメッセージを挿入する最初の作成、新しい`CloudQueueMessage`します。 次に、呼び出し、`AddMessage`メソッド。 A `CloudQueueMessage` (utf-8 形式) の文字列にいずれかから作成できる、または`byte`、このような配列。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>次のメッセージをピークします。

キューの先頭にあるメッセージをピークを呼び出して、キューから削除することがなく、`PeekMessage`メソッド。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>処理のための次のメッセージを取得します。

処理のため、キューの先頭にあるメッセージを取得するには呼び出すことによって、`GetMessage`メソッド。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

使用して、メッセージを正常に処理を後で示す`DeleteMessage`します。

## <a name="change-the-contents-of-a-queued-message"></a>キューに置かれたメッセージの内容を変更します。

取得したメッセージでインプレースでキューの内容を変更することができます。 メッセージが作業タスクである場合は、作業のタスクの状態を更新するこの機能を使用する可能性があります。 次のコードでは、新しい内容で、キュー メッセージを更新し、表示タイムアウトを 60 秒延長を設定します。 これは、メッセージに関連付けられた作業の状態を保存され、クライアントは、メッセージの作業を続行する時間が 1 分。 この手法は、ハードウェアまたはソフトウェアの障害により、処理手順が失敗した場合、最初からやり直すことがなく、キュー メッセージに対して複数のステップのワークフローを追跡するために使用できます。 同様に、再試行回数を保持して、削除する場合は、メッセージが再試行される回数のいくつかの数よりも多く、通常、します。 これは、それが処理されるたびに、アプリケーション エラーをトリガーするメッセージから保護されます。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>次のメッセージをデキューします。

コードは、キューの 2 つの手順でキューからメッセージ。 呼び出すと`GetMessage`キュー内の次のメッセージを取得します。 返されたメッセージ`GetMessage`このキューからメッセージを読み取る他のコードを非表示になります。 既定では、このメッセージでは 30 秒間非表示に残ります。 キューからのメッセージの削除を完了する必要がありますも呼び出す`DeleteMessage`します。 メッセージを削除するには、この 2 段階プロセスでは、コードは、ハードウェアまたはソフトウェアの障害のためのメッセージの処理に失敗すると、コードの別のインスタンスは同じメッセージを取得し、もう一度お試しことを保証します。 コードの呼び出し`DeleteMessage`メッセージが処理された直後します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>一般的な Queue storage Api を使用して非同期ワークフロー

この例では、一般的なキュー ストレージ Api で、非同期ワークフローを使用する方法を示します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>メッセージのデキューの追加オプション

キューからメッセージの取得をカスタマイズする 2 つの方法はあります。
最初に、(最大 32 個) のメッセージのバッチを取得できます。 次に、長いまたは短いの非表示タイムアウトを設定する、詳細や、各メッセージを完全に処理にかかる時間が、コードをできるようにします。 次のコード例では`GetMessages`20 を取得する 1 つのメッセージを呼び出すし、各メッセージを処理します。 また、メッセージごとに 5 分間に非表示タイムアウトを設定します。 5 分以内に、すべてのメッセージに対して同時に、同時に開始するため 5 分が経過の呼び出し以降に`GetMessages`、削除されていないすべてのメッセージが再び表示されます。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>キューの長さを取得します。

キューにメッセージの数の推定値を取得できます。 `FetchAttributes`メソッドは、メッセージ数など、キューの属性を取得する Queue サービスを要求します。 `ApproximateMessageCount`によって取得された最後の値を返します、`FetchAttributes`メソッドを呼び出さずに、キュー サービス。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>キューを削除します。

キューおよびそれに含まれるすべてのメッセージを削除する、`Delete`キュー オブジェクトのメソッド。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>次の手順

これで、Queue storage の基本を学習するには、以下のリンクより複雑なストレージ タスクについて説明しますに従います。

- [.NET 用 azure Storage Api](/dotnet/api/overview/azure/storage)
- [Azure Storage 型プロバイダー](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure Storage チーム ブログ](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure Storage 接続文字列を構成します。](/azure/storage/common/storage-configure-connection-string)
- [Azure ストレージ サービス REST API リファレンス](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
