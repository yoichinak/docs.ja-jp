---
title: F# を使用した Azure Blob Storage の概要
description: Azure Blob storage を使用して、非構造化データをクラウドに格納します。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c765f38cba7642e813a5966d3b7754c5ce45abbd
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107122"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F を使用して Azure Blob storage を使ってみる\#

Azure BLOB Storage は、非構造化データをオブジェクト/BLOB としてクラウドに格納するサービスです。 Blob Storage は、ドキュメント、メディア ファイル、アプリケーション インストーラーなど、任意の種類のテキストまたはバイナリ データを格納できます。 Blob Storage は、オブジェクト ストレージとも呼ばれます。

この記事では、Blob storage を使用して一般的なタスクを実行する方法について説明します。 サンプルは、.NET 用 Azure Storage クライアント ライブラリを使用した F# を使用して記述します。 説明するタスクには、blob のアップロード、一覧表示、ダウンロード、および削除の方法が含まれます。

Blob storage の概念の概要については、「 [.net ガイド](/azure/storage/storage-dotnet-how-to-use-blobs)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するには、最初に[Azure ストレージアカウントを作成](/azure/storage/storage-create-storage-account)する必要があります。 また、このアカウントのストレージアクセスキーも必要です。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成して、F# スクリプトと開始 F# 対話型

この記事のサンプルは、F# アプリケーションまたは F# スクリプトのいずれかで使用できます。 F# スクリプトを作成するには、ファイルを作成、`.fsx`拡張機能の例では、 `blobs.fsx`、F# 開発環境にします。

次に、[パケット](https://fsprojects.github.io/Paket/)や`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)などの[パッケージマネージャー](package-management.md)を使用して、 `Microsoft.WindowsAzure.ConfigurationManager` `#r`ディレクティブを使用し`Microsoft.WindowsAzure.Configuration.dll`て、パッケージとパッケージをインストールし、スクリプトにおよびを参照`WindowsAzure.Storage.dll`します。

### <a name="add-namespace-declarations"></a>名前空間宣言を追加する

ファイルの先頭`open`に次のステートメントを追加します。 `blobs.fsx`

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得する

このチュートリアルでは、Azure Storage 接続文字列が必要です。 接続文字列の詳細については、「[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)」を参照してください。

このチュートリアルでは、次のように、スクリプトに接続文字列を入力します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

ただし、実際のプロジェクトではこの方法は**お勧めできません**。 ストレージアカウントキーは、ストレージアカウントのルートパスワードに似ています。 ストレージアカウントキーは常に慎重に保護してください。 他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーンテキストファイルに保存したりしないでください。 侵害された可能性があると思われる場合は、Azure ポータルを使用してキーを再生成することができます。

実際のアプリケーションでは、ストレージ接続文字列を維持する最善の方法は構成ファイルにあります。 構成ファイルから接続文字列を取得するには、次の手順を実行します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure Configuration Manager の使用は省略可能です。 .NET Framework の`ConfigurationManager`型などの API を使用することもできます。

### <a name="parse-the-connection-string"></a>接続文字列を解析する

接続文字列を解析するには、次のように指定します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

これにより`CloudStorageAccount`、が返されます。

### <a name="create-some-local-dummy-data"></a>いくつかのローカルダミーデータを作成する

開始する前に、スクリプトのディレクトリにダミーのローカルデータを作成します。 後でこのデータをアップロードします。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob service クライアントを作成する

型`CloudBlobClient`を使用すると、blob ストレージに格納されているコンテナーと blob を取得できます。 サービスクライアントを作成する方法の1つを次に示します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

これで、Blob storage との間でデータを読み取り、データを書き込むコードを記述する準備ができました。

## <a name="create-a-container"></a>コンテナーの作成

この例では、コンテナーがまだ存在しない場合に作成する方法を示します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

既定では、新しいコンテナーはプライベートです。つまり、このコンテナーから blob をダウンロードするには、ストレージアクセスキーを指定する必要があります。 コンテナー内のファイルをすべてのユーザーが使用できるようにする場合は、次のコードを使用して、コンテナーをパブリックに設定できます。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

パブリックコンテナー内の blob は、インターネット上のすべてのユーザーが表示できますが、変更または削除するには、適切なアカウントアクセスキーまたは共有アクセス署名がある必要があります。

## <a name="upload-a-blob-into-a-container"></a>コンテナーへの blob のアップロード

Azure Blob Storage は、ブロック blob とページ blob をサポートしています。 ほとんどの場合、ブロック blob を使用することをお勧めします。

ファイルをブロック blob にアップロードするには、コンテナー参照を取得し、それを使用してブロック blob 参照を取得します。 Blob の参照を取得したら、 `UploadFromFile`メソッドを呼び出すことによって、データの任意のストリームをアップロードできます。 この操作では、blob が既に存在していない場合は作成し、存在する場合は上書きします。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>コンテナー内の blob を一覧表示する

コンテナー内の blob を一覧表示するには、最初にコンテナー参照を取得します。 その後、コンテナーの`ListBlobs`メソッドを使用して、その中の blob やディレクトリを取得できます。 返される`IListBlobItem`の豊富なプロパティおよびメソッドのセットにアクセスするには`CloudBlockBlob`、それを、 `CloudPageBlob`、または`CloudBlobDirectory`オブジェクトにキャストする必要があります。 型が不明な場合は、型チェックを使用して、キャスト先を決定できます。 次のコードは、 `mydata`コンテナー内の各項目の URI を取得して出力する方法を示しています。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Blob には、名前にパス情報を指定することもできます。 これにより、従来のファイルシステムと同じように整理および走査できる仮想ディレクトリ構造が作成されます。 ディレクトリ構造は仮想のみであり、Blob storage で使用できるリソースはコンテナーと blob のみであることに注意してください。 ただし、ストレージクライアントライブラリは、仮想`CloudBlobDirectory`ディレクトリを参照するオブジェクトを提供し、この方法で構成されている blob を操作するプロセスを簡略化します。

たとえば、という名前`photos`のコンテナー内の次の一連のブロック blob について考えてみます。

*photo1.jpg*\
*2015/architecture/description .txt*\
*2015/architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/architecture/photo5.jpg*\
*2016/architecture/photo6.jpg*\
*2016/architecture/description .txt*\
*2016/photo7.jpg*\

コンテナーでを`ListBlobs`呼び出すと (上記のサンプルのように)、階層化された一覧が返されます。 コンテナー内のディレクトリ`CloudBlobDirectory`と`CloudBlockBlob` blob をそれぞれ表すオブジェクトとオブジェクトの両方が含まれている場合、結果の出力は次のようになります。

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

必要に応じて、 `UseFlatBlobListing` `ListBlobs`メソッドのパラメーターをに`true`設定できます。 この場合、コンテナー内のすべての blob が`CloudBlockBlob`オブジェクトとして返されます。 フラットリストを`ListBlobs`返すためのの呼び出しは次のようになります。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

また、コンテナーの現在の内容によっては、結果は次のようになります。

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a>Blob のダウンロード

Blob をダウンロードするには、まず blob の参照を取得`DownloadToStream`してから、メソッドを呼び出します。 次の例では`DownloadToStream` 、メソッドを使用して、ローカルファイルに永続化できるストリームオブジェクトに blob の内容を転送します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

`DownloadToStream`メソッドを使用して、blob の内容をテキスト文字列としてダウンロードすることもできます。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Blob の削除

Blob を削除するには、まず blob の参照を取得し`Delete` 、次にそのメソッドを呼び出します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>ページ内の blob を非同期に一覧表示する

多数の blob を一覧表示する場合、または1つのリスティング操作で返す結果の数を制御する場合は、結果ページに blob を一覧表示できます。 この例では、大量の結果を返すために待機している間に実行がブロックされないように、結果をページ単位で非同期的に返す方法を示します。

この例はフラット blob リストを示していますが、 `useFlatBlobListing` `ListBlobsSegmentedAsync`メソッドのパラメーターをに設定する`false`ことによって、階層化された一覧を作成することもできます。

このサンプルでは、 `async`ブロックを使用して非同期メソッドを定義します。 キーワード``let!``は、リスティングタスクが完了するまで、サンプルメソッドの実行を中断します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

次のように、この非同期ルーチンを使用できるようになりました。 まずダミーデータをアップロードします (このチュートリアルで既に作成したローカルファイルを使用します)。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

ここで、ルーチンを呼び出します。 非同期操作`Async.RunSynchronously`の実行を強制するには、を使用します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>追加 blob への書き込み

追加 blob は、ログ記録などの追加操作用に最適化されています。 ブロック blob と同様に、追加 blob はブロックで構成されますが、追加 blob に新しいブロックを追加すると、常に blob の末尾に追加されます。 追加 blob の既存のブロックを更新または削除することはできません。 追加 blob のブロック Id は、ブロック blob のブロック Id として公開されません。

追加 blob 内の各ブロックは、最大 4 MB までの異なるサイズにすることができ、追加 blob には最大5万のブロックを含めることができます。 このため、追加 blob の最大サイズは 195 GB (4 MB X 5万ブロック) よりも少し大きくなります。

次の例では、新しい追加 blob を作成し、データを追加して、単純なログ記録操作をシミュレートします。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

3種類の blob の相違点の詳細については、「[ブロック blob、ページ blob、および追加 blob](https://msdn.microsoft.com/library/azure/ee691964.aspx)について」を参照してください。

## <a name="concurrent-access"></a>同時アクセス

複数のクライアントまたは複数のプロセスインスタンスからの blob への同時アクセスをサポートするには、 **etag**または**リース**を使用できます。

- **Etag** -blob またはコンテナーが別のプロセスによって変更されたことを検出する方法を提供します。

- **リース**-一定期間、blob への排他、更新、書き込み、または削除のアクセス権を取得する方法を提供します。

詳細については、「 [Microsoft Azure Storage での同時実行の管理](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)」を参照してください。

## <a name="naming-containers"></a>コンテナーの名前付け

Azure storage 内のすべての blob は、コンテナー内に存在する必要があります。 コンテナーは、blob 名の一部を形成します。 たとえば、は`mydata` 、次のサンプル blob uri のコンテナーの名前です。

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

コンテナー名は、次の名前付け規則に準拠した有効な DNS 名である必要があります。

1. コンテナー名の先頭には文字または数字を使用する必要があり、文字、数字、ダッシュ (-) 文字のみを含めることができます。
1. すべてのダッシュ (-) 文字は、その直後に文字または数字を付ける必要があります。連続するダッシュは、コンテナー名では使用できません。
1. コンテナー名のすべての文字は、小文字にする必要があります。
1. コンテナー名は、3 ~ 63 文字の長さにする必要があります。

コンテナーの名前は常に小文字にする必要があることに注意してください。 コンテナー名に大文字を含める場合や、コンテナーの名前付け規則に違反する場合は、400エラー (無効な要求) が発生することがあります。

## <a name="managing-security-for-blobs"></a>Blob のセキュリティを管理する

既定では、アカウントの所有者にアクセスを制限することで、アカウントのアクセスキーを所有しているユーザーに対して、Azure Storage のデータのセキュリティを保護します。 ストレージアカウントで blob データを共有する必要がある場合は、アカウントアクセスキーのセキュリティを損なうことなくこの操作を行うことが重要です。 さらに、blob データを暗号化して、ネットワーク上および Azure Storage で安全に保護されるようにすることもできます。

### <a name="controlling-access-to-blob-data"></a>Blob データへのアクセスの制御

既定では、ストレージアカウントの blob データには、ストレージアカウントの所有者のみがアクセスできます。 Blob ストレージに対する要求の認証には、既定でアカウントアクセスキーが必要です。 ただし、特定の blob データを他のユーザーが使用できるようにすることもできます。

### <a name="encrypting-blob-data"></a>Blob データの暗号化

Azure Storage は、クライアントとサーバーの両方で blob データの暗号化をサポートしています。

## <a name="next-steps"></a>次の手順

これで、Blob storage の基本を学習できました。詳細については、次のリンク先を参照してください。

### <a name="tools"></a>ツール

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Blob F# 、テーブル、およびキュー Azure Storage 資産を探索し、それらに対して CRUD 操作を簡単に適用するために使用できる型プロバイダー。

- [Fsharp.core](https://github.com/fsprojects/FSharp.Azure.Storage)\
Microsoft Azure F# Table Storage サービスを使用するための API

- [Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Windows、OS X、Linux で Azure Storage データを視覚的に操作できる Microsoft 製の無料のスタンドアロンアプリです。

### <a name="blob-storage-reference"></a>Blob ストレージのリファレンス

- [.NET 用 Api の Azure Storage](/dotnet/api/overview/azure/storage)
- [Azure Storage Services REST API リファレンス](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>関連ガイド

- [Azure Blob Storage でのはじめにC#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Windows で AzCopy コマンドラインユーティリティを使用してデータを転送する](/azure/storage/common/storage-use-azcopy)
- [Linux で AzCopy コマンドラインユーティリティを使用してデータを転送する](/azure/storage/common/storage-use-azcopy-linux)
- [Azure Storage 接続文字列を構成する](/azure/storage/common/storage-configure-connection-string)
- [Azure Storage チームのブログ](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [クイック スタート:.NET を使用してオブジェクトストレージに blob を作成する](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
