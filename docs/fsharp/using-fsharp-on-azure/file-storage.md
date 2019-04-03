---
title: F# を使用した Azure File Storage の概要
description: Azure File storage を使用してクラウドにファイル データを格納し、Azure の仮想マシン (VM) からクラウド ファイル共有をマウントまたはオンプレミス アプリケーションから Windows を実行しています。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fa6dadc863bb9116cfac5afd7cd22a724bc7afe2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969597"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>F を使用した Azure File storage を概要します。\#

Azure File storage は、標準を使用して、クラウド内のファイル共有を提供するサービスで[サーバー メッセージ ブロック (SMB) プロトコル](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)します。 SMB 2.1 と SMB 3.0 の両方がサポートされています。 Azure File storage を使用には、迅速かつコストのかかる書き換えを行わずに、azure ファイル共有に依存するレガシ アプリケーションを移行することができます。 または、オンプレミスのクライアントから Azure 仮想マシンまたはクラウド サービスで実行しているアプリケーションは、デスクトップ アプリケーションの一般的な SMB 共有をマウントすると同様に、クラウド内のファイル共有をマウントできます。 任意の数のアプリケーション コンポーネントのマウントし、同時に、File storage 共有にアクセスします。

File storage の概念的概要についてを参照してください[file storage 用の .NET ガイド](/azure/storage/storage-dotnet-how-to-use-files)します。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成](/azure/storage/storage-create-storage-account)です。
このアカウントのストレージ アクセス キーも必要になります。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成して、F# スクリプトと開始 F# 対話型

この記事のサンプルは、F# アプリケーションまたは F# スクリプトのいずれかで使用できます。 F# スクリプトを作成するには、ファイルを作成、`.fsx`拡張機能の例では、 `files.fsx`、F# 開発環境にします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケット](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブ。

### <a name="add-namespace-declarations"></a>名前空間宣言を追加します。

次の追加`open`ステートメントの先頭に、`files.fsx`ファイル。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得します。

このチュートリアルでは、Azure Storage 接続文字列を必要があります。 接続文字列の詳細については、[ストレージ接続文字列を構成](/azure/storage/storage-configure-connection-string)を参照してください。

チュートリアルでは、次のように、スクリプトで、接続文字列を入力します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

ただし、これは**しないで**の実際のプロジェクト。 ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存することは、他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure Portal を使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージ接続文字列を維持するために最善の方法は、構成ファイルです。 構成ファイルから接続文字列を取得するには、は、これを行うことができます。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure Configuration Manager の使用は省略可能です。 .NET Framework のなどの API を使用することもできます。`ConfigurationManager`型。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のように使用します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

これにより返されます、`CloudStorageAccount`します。

### <a name="create-the-file-service-client"></a>ファイル サービス クライアントを作成します。

`CloudFileClient`型では、File storage に格納されたファイルをプログラムで使用することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

File storage からデータを読み書きするコードを記述する準備が整いました。

## <a name="create-a-file-share"></a>ファイル共有を作成します。

この例では、存在しない場合は、ファイル共有を作成する方法を示します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>ルート ディレクトリとサブディレクトリを作成します。

ここでは、ルート ディレクトリを取得するルートのサブディレクトリを取得します。 まだ存在しない場合は、どちらもタイプを作成します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>テキストをファイルとしてアップロードします。

この例では、テキストとしてファイルをアップロードする方法を示します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>ファイル、ファイルのローカル コピーをダウンロードします。

ここでは、ローカル ファイルに内容を追加、先ほど作成したファイルをダウンロードします。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>ファイル共有の最大サイズを設定します。

次の例では、共有の現在の使用状況を確認して、共有のクォータを設定する方法を示します。 `FetchAttributes` 共有の設定を呼び出す必要がある`Properties`、および`SetProperties`Azure File storage にローカルの変更を反映します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>ファイルまたはファイル共有の共有アクセス署名を生成します。

ファイル共有または個々 のファイルの shared access signature (SAS) を生成することができます。 Shared access signature を管理するファイル共有に共有アクセス ポリシーを作成することもできます。 共有アクセス ポリシーの作成は推奨、それが侵害された場合は、SAS を取り消す手段を提供します。

ここで、作成、共有、共有上のポリシーにアクセスし、そのポリシーを使用して、共有内のファイルを SAS に制約を指定します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

作成と共有アクセス署名の使用に関する詳細については、[を使用して Shared Access Signature (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1)と[の作成と使用して SAS を Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2)を参照してください。

### <a name="copy-files"></a>ファイルのコピー

ファイルを別のファイルまたは blob または blob にファイルをコピーできます。 ファイルまたは blob をファイルに blob をコピーする場合を*する必要があります*同じストレージ アカウント内にコピーする場合でも、ソース オブジェクトを認証する共有アクセス署名 (SAS) を使用します。

### <a name="copy-a-file-to-another-file"></a>ファイルを別のファイルにコピーします。

ここでは、同じ共有内の別のファイルにファイルをコピーします。 このコピー操作は、同じストレージ アカウント内のファイルをコピーするので、コピーを実行するのに共有キー認証を使用することができます。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>ファイルを blob にコピーします。

ここでは、ファイルを作成して、同じストレージ アカウント内の blob にコピーします。 コピー操作中にソース ファイルへのアクセスを認証するサービスを使用するソース ファイルの SAS を作成します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

同じ方法でファイルに blob をコピーすることができます。 ソース オブジェクトが blob の場合は、コピー操作中にその blob へのアクセスの認証に SAS を作成します。

## <a name="troubleshooting-file-storage-using-metrics"></a>メトリックを使用して File storage のトラブルシューティング

Azure Storage Analytics は、File storage のメトリックをサポートします。 メトリック データを要求のトレースでき、問題を診断できます。

File storage のメトリックを有効にすることができます、 [Azure Portal](https://portal.azure.com)から実行できますかF#次のように。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>次の手順

Azure File storage の詳細については、これらのリンクを参照してください。

### <a name="conceptual-articles-and-videos"></a>概念に関する記事とビデオ

- [Windows および Linux 用の azure File Storage: 円滑なクラウド SMB ファイル システム](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Linux で Azure File Storage を使用する方法](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>File storage のツールのサポート

- [Azure Storage で Azure PowerShell の使用](/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Storage で AzCopy を使用する方法](/azure/storage/storage-use-azcopy)
- [Azure Storage で Azure CLI の使用](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>参照

- [.NET リファレンス用ストレージ クライアント ライブラリ](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [ファイル サービス REST API リファレンス](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>ブログの投稿

- [Azure File storage の一般提供開始](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Inside Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Microsoft Azure File Service の概要](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Microsoft Azure Files への接続の維持](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
