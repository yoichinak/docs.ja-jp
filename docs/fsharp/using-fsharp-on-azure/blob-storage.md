---
title: F# を使用した Azure Blob Storage の概要
description: Azure Blob storage を使用してクラウドでは、非構造化データを格納します。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 62178edf22ad48d0388f34488b68d135068d50a2
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846429"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F を使用した Azure Blob storage を概要します。\#

Azure BLOB Storage は、非構造化データをオブジェクト/BLOB としてクラウドに格納するサービスです。 Blob Storage は、ドキュメント、メディア ファイル、アプリケーション インストーラーなど、任意の種類のテキストまたはバイナリ データを格納できます。 Blob Storage は、オブジェクト ストレージとも呼ばれます。

この記事では、Blob storage を使用して一般的なタスクを実行する方法を示します。 サンプルは、.NET 用 Azure Storage クライアント ライブラリを使用した F# を使用して記述します。 対象タスクには、アップロード、一覧表示、ダウンロード、および blob を削除する方法が含まれます。

Blob storage の概念的概要については、[blob ストレージ用の .NET ガイド](/azure/storage/storage-dotnet-how-to-use-blobs)を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成](/azure/storage/storage-create-storage-account)です。 このアカウントのストレージ アクセス キーも必要があります。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成して、F# スクリプトと開始 F# 対話型

この記事のサンプルは、F# アプリケーションまたは F# スクリプトのいずれかで使用できます。 F# スクリプトを作成するには、ファイルを作成、`.fsx`拡張機能の例では、 `blobs.fsx`、F# 開発環境にします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケット](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`と`Microsoft.WindowsAzure.ConfigurationManager`パッケージと参照`WindowsAzure.Storage.dll`と`Microsoft.WindowsAzure.Configuration.dll`を使用して、スクリプト、`#r`ディレクティブ。

### <a name="add-namespace-declarations"></a>名前空間宣言を追加します。

次の追加`open`ステートメントの先頭に、`blobs.fsx`ファイル。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得します。

このチュートリアルに Azure Storage の接続文字列が必要です。 接続文字列の詳細については、[ストレージ接続文字列を構成](/azure/storage/storage-configure-connection-string)を参照してください。

このチュートリアルでは、次のように、スクリプトで、接続文字列を入力します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

ただし、これは**しないで**の実際のプロジェクト。 ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存することは、他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure Portal を使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージ接続文字列を維持するために最善の方法は、構成ファイルです。 構成ファイルから接続文字列を取得するには、は、これを行うことができます。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure Configuration Manager の使用は省略可能です。 .NET Framework のなどの API を使用することもできます。`ConfigurationManager`型。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のように使用します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

これにより返されます、`CloudStorageAccount`します。

### <a name="create-some-local-dummy-data"></a>ローカルのダミー データの一部を作成します。

開始する前に、スクリプトのディレクトリにダミーのローカル データの一部を作成します。 後でこのデータをアップロードします。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob service クライアントを作成します。

`CloudBlobClient`型では、コンテナーと Blob storage に格納されている blob を取得することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

データを読み取るし、Blob storage にデータを書き込むコードを記述する準備が整いました。

## <a name="create-a-container"></a>コンテナーの作成

この例では、存在しない場合は、コンテナーを作成する方法を示します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

既定では、新しいコンテナーはプライベートでは、このコンテナーから blob をダウンロードするストレージ アクセス キーを指定することを意味します。 すべてのユーザーがコンテナー内のファイルを使用できるようにする場合は、次のコードを使用して公開するコンテナーを設定できます。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

インターネット ユーザー全員、パブリック コンテナー内の blob を表示することができますが、適切なアカウント アクセス キーまたは共有アクセス署名がある場合にのみ、それらを削除または変更できます。

## <a name="upload-a-blob-into-a-container"></a>Blob コンテナーをアップロードします。

Azure Blob Storage には、ブロック blob とページ blob がサポートしています。 ほとんどの場合、ブロック blob とは、使用する推奨される型です。

ブロック blob にファイルをアップロードするには、コンテナーの参照を取得し、それを使用して、ブロック blob の参照を取得します。 Blob の参照を作成したら、アップロードできますデータの任意のストリームを呼び出すことによって、`UploadFromFile`メソッド。 この操作は、blob を作成しますしなかった以前存在か存在する場合に上書きします。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>コンテナー内の blob を一覧表示します。

コンテナー内の blob を一覧表示、まずコンテナーの参照を取得します。 コンテナーを使用することができますし、 `ListBlobs` blob やその中のディレクトリを取得します。 プロパティと返されるメソッドの豊富なセットにアクセスする`IListBlobItem`にキャストする必要があります、 `CloudBlockBlob`、 `CloudPageBlob`、または`CloudBlobDirectory`オブジェクト。 型が既知でない場合は、判断にキャストするために型チェックを使用できます。 次のコードを取得して内の各項目の URI を出力する方法を示して、`mydata`コンテナー。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

名前の blob、名前にパス情報を使用することもできます。 これにより、整理して従来のファイル システムと同様に走査する仮想ディレクトリ構造が作成されます。 ディレクトリ構造は仮想のみ - Blob storage で使用できる唯一のリソースはコンテナーと blob のことに注意してください。 ただし、ストレージ クライアント ライブラリが用意されています、`CloudBlobDirectory`オブジェクトの仮想ディレクトリを参照し、この方法で編成されている blob の操作プロセスを簡略化します。

たとえば、次の一連のブロック blob という名前のコンテナーで`photos`:

*photo1.jpg*\
*2015/architecture/description.txt*\
*2015/architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/architecture/photo5.jpg*\
*2016/architecture/photo6.jpg*\
*2016/architecture/description.txt*\
*2016/photo7.jpg*\

呼び出すと`ListBlobs`(上記のサンプル) のように、コンテナーに対して、階層化された一覧が返されます。 両方が含まれる場合`CloudBlobDirectory`と`CloudBlockBlob`し、次のように、結果の出力ディレクトリと、コンテナー内の blob をそれぞれ表すオブジェクト。

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

必要に応じて、設定することができます、`UseFlatBlobListing`のパラメーター、`ListBlobs`メソッドを`true`します。 この場合、コンテナー内のすべての blob として返されます、`CloudBlockBlob`オブジェクト。 呼び出し`ListBlobs`を次のようなフラットな一覧を返します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

また、よう、コンテナーの現在の内容に応じて、結果になります。

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

## <a name="download-blobs"></a>Blob をダウンロードします。

Blob をダウンロードするには、まず blob の参照を取得を呼び出して、`DownloadToStream`メソッド。 次の例では、`DownloadToStream`ローカル ファイルに保存できるストリーム オブジェクトに blob の内容を転送する方法。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

使用することも、`DownloadToStream`メソッドを文字列としての blob のコンテンツをダウンロードします。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Blob を削除します。

Blob を削除するには、まず blob の参照を取得を呼び出して、`Delete`メソッド。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>非同期的にページ内の blob を一覧表示します。

大規模な数の blob を一覧表示、または 1 つの一覧作成操作で返される結果の数を制御する場合、結果のページ内の blob を一覧表示できます。 この例は、大量の結果セットを返すを待機中には実行がブロックされないように、ページで、非同期的に結果を返す方法を示します。

この例の一覧を表示すると、blob をフラット、設定して、階層的な一覧についてを実行することもできますが、`useFlatBlobListing`のパラメーター、`ListBlobsSegmentedAsync`メソッドを`false`します。

非同期のメソッドを定義するサンプルを使用して、`async`ブロックします。 ``let!``キーワードは、一覧表示タスクが完了するまでに、サンプル メソッドの実行を中断します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

この非同期ルーチンを次のように使用できますようになりました。 最初に、一部のダミー データ (このチュートリアルで前に作成されたローカル ファイルを使用) をアップロードします。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

ここで、ルーチンを呼び出します。 使用する`Async.RunSynchronously`非同期操作の実行を強制します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>追加 blob への書き込み

追加 blob は、ログ記録などの追加操作のために最適化されます。 ブロック blob、追加 blob はブロックで構成されますが、blob の末尾に必ず追加される追加 blob に新しいブロックを追加するとします。 更新または追加 blob の既存のブロックを削除することはできません。 ブロック blob は、追加 blob のブロック Id は公開されません。

追加 blob 内の各ブロックは、最大 4 MB までのさまざまなサイズ、追加 blob は最大 50,000 のブロックを含めることができます。 追加 blob の最大サイズは 195 GB (4 MB X 50,000 ブロック) よりも少しではそのためです。

次の例では、新しい追加 blob を作成し、簡単なログ記録操作をシミュレートするのには、いくつかのデータを追加します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

参照してください[ブロック Blob、ページ Blob、および追加 Blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) blob の 3 つの種類の違いの詳細についてはします。

## <a name="concurrent-access"></a>同時実行のアクセス

使用することができますから複数のクライアントまたは複数のプロセス インスタンスを blob への同時アクセスをサポートする**Etag**または**リース**します。

* **Etag** -blob またはコンテナーが別のプロセスによって変更されたことを検出する手段を提供します。

* **リース**の取得だけで、更新可能な書き込みまたは一定期間、blob へのアクセスを削除する方法を提供します。

詳細については、[Microsoft Azure Storage 内の同時実行を管理する](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)を参照してください。

## <a name="naming-containers"></a>名前付けコンテナー

Azure storage 内のすべての blob は、コンテナー内に存在する必要があります。 コンテナーは、blob 名の一部を形成します。 たとえば、`mydata`これらサンプル blob Uri 内のコンテナーの名前を指定します。

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

コンテナー名は、次の名前付け規則に準拠している、有効な DNS 名である必要があります。

1. コンテナー名は英字または数字で始まらなければなりませんし、文字、数字、およびダッシュ (-) 文字のみを含めることができます。
1. すべてのダッシュ (-) 文字はすぐに前し、後にアルファベットまたは数字; する必要があります。コンテナー名では、連続するダッシュは許可されていません。
1. コンテナー名のすべての文字を小文字にする必要があります。
1. コンテナー名は 3 ~ 63 文字にする必要があります。

コンテナーの名前が小文字に常にする必要がありますに注意してください。 コンテナー名に、大文字を含めるか、それ以外の場合、コンテナーの名前付け規則に違反した場合 400 (Bad Request) エラーが発生する可能性があります。

## <a name="managing-security-for-blobs"></a>Blob のセキュリティを管理します。

既定では、Azure Storage のデータはセキュリティを維持は、アカウント アクセス キーを所有しているユーザー アカウントの所有者へのアクセスを制限することで。 ストレージ アカウント内の blob データを共有する必要がある場合は、アカウント アクセス キーのセキュリティを損なうことがなく行う必要があります。 さらに、ネットワーク経由でと、Azure Storage に安全であることを確認する blob データを暗号化できます。

### <a name="controlling-access-to-blob-data"></a>Blob データへのアクセスを制御します。

既定では、ストレージ アカウント内の blob データはストレージ アカウント所有者のみがアクセスできます。 Blob storage に対する要求の認証には、既定では、アカウント アクセス キーが必要です。 ただし、特定の blob データを他のユーザーが利用できるようにする場合があります。

### <a name="encrypting-blob-data"></a>Blob データの暗号化

Azure Storage では、クライアントとサーバーの両方の blob データの暗号化をサポートします。

## <a name="next-steps"></a>次の手順

これで、Blob storage の基本を学習するは詳細については、これらのリンクに従います。

### <a name="tools"></a>ツール

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
F#型プロバイダーが Blob、Table、および Azure Storage のキューの資産を探索し、それらに対する CRUD 操作を簡単に適用するために使用できます。

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F# Microsoft Azure Table Storage サービスを使用するための API

- [Microsoft Azure ストレージ エクスプ ローラー (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Microsoft Windows、OS X、Linux で Azure Storage のデータを視覚的に作業することができます、無料のスタンドアロン アプリです。

### <a name="blob-storage-reference"></a>Blob ストレージのリファレンス

- [.NET 用 azure Storage Api](/dotnet/api/overview/azure/storage)
- [Azure ストレージ サービス REST API リファレンス](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>関連ガイド

- [C# での Azure Blob Storage の概要](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Windows 上の AzCopy コマンド ライン ユーティリティを使用したデータを転送します。](/azure/storage/common/storage-use-azcopy)
- [Linux 上の AzCopy コマンド ライン ユーティリティを使用したデータを転送します。](/azure/storage/common/storage-use-azcopy-linux)
- [Azure Storage 接続文字列を構成します。](/azure/storage/common/storage-configure-connection-string)
- [Azure Storage チーム ブログ](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [クイック スタート:.NET を使用してオブジェクト ストレージに blob を作成するには](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
