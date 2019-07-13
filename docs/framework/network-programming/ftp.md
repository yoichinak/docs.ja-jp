---
title: FTP - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 90775b20343b6ad831af6f5380f8ab7553abb16b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54186151"
---
# <a name="ftp"></a>FTP

.NET Framework は、<xref:System.Net.FtpWebRequest> クラスと <xref:System.Net.FtpWebResponse> クラスを使用して、FTP プロトコルの包括的なサポートを提供します。 これらのクラスは <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> から派生します。 ほとんどの場合、<xref:System.Net.WebRequest> クラスと <xref:System.Net.WebResponse> クラスは、要求を行うために必要なすべてを提供しますが、プロパティとして公開されている FTP 固有の機能にアクセスする必要がある場合は、これらのクラスを <xref:System.Net.FtpWebRequest> または <xref:System.Net.FtpWebResponse> に型キャストすることができます。

## <a name="examples"></a>使用例

詳細については、次のトピックを参照してください。[方法: FTP を使用してファイルをダウンロードする](how-to-download-files-with-ftp.md)、[方法:FTP を使用してファイルをアップロードする](how-to-upload-files-with-ftp.md)、[方法:FTP でディレクトリの内容を一覧表示する](how-to-list-directory-contents-with-ftp.md)。

## <a name="ftp-and-proxies"></a>FTP とプロキシ

(<xref:System.Net.FtpWebRequest.Proxy%2A> プロパティで指定された) プロキシが HTTP プロキシの場合、<xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、<xref:System.Net.WebRequestMethods.Ftp.ListDirectory>、および <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> コマンドのみがサポートされます。

## <a name="see-also"></a>関連項目

- [プロキシを介したインターネットへのアクセス](accessing-the-internet-through-a-proxy.md)
- [ネットワーク プログラミングのサンプル](network-programming-samples.md)
- [アプリケーション プロトコルの使用](using-application-protocols.md)
