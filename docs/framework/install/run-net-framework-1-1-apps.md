---
title: Windows 8、Windows 8.1、または Windows 10 での .NET Framework 1.1 アプリの実行
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aae87b60e207ebe406e863f123e1dc3e56aeb4f7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051937"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Windows 8、Windows 8.1、または Windows 10 での .NET Framework 1.1 アプリの実行

.NET Framework 1.1 は、[!INCLUDE[win8](../../../includes/win8-md.md)]、[!INCLUDE[win81](../../../includes/win81-md.md)]、[!INCLUDE[winserver8](../../../includes/winserver8-md.md)]、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]、または Windows 10 の各オペレーティング システムではサポートされていません。 場合によっては、アプリケーションの実行に .NET Framework 1.1 が特別に指定されています。 このような場合は、.NET Framework 3.5 SP1 以降のバージョンで実行するためにアプリケーションをアップグレードするように、独立ソフトウェア ベンダー (ISV) に連絡する必要があります。 詳細については、「[.NET Framework 1.1 からの移行](../migration-guide/migrating-from-the-net-framework-1-1.md)」を参照してください。

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>CD またはダウンロード センターからの .NET Framework 1.1 のインストール

[!INCLUDE[win8](../../../includes/win8-md.md)]、[!INCLUDE[win81](../../../includes/win81-md.md)]、[!INCLUDE[winserver8](../../../includes/winserver8-md.md)]、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]、または Windows 10 に .NET Framework 1.1 を手動でインストールすることはできません。 サポート対象から除外されました。 パッケージをインストールしようとすると、「このバージョンの .NET Framework は以前にインストールしたバージョンと互換性がないため、セットアップを続行できません。」というエラー メッセージが表示されます。 この問題を解決するには、[.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22) をインストールします。 このバージョンには .NET Framework 2.0 (.NET Framework 1.1 の次のリリース) が含まれており、これは [!INCLUDE[win8](../../../includes/win8-md.md)]、[!INCLUDE[win81](../../../includes/win81-md.md)]、および Windows 10 でサポートされています。 .NET Framework の新しいバージョンに自動的に更新されるかどうかを確認するために、常に最初にアプリケーションのインストールを試す必要があります。 更新されない場合は、アプリケーションの更新について ISV に連絡してください。

## <a name="see-also"></a>関連項目

- [.NET Framework 1.1 からの移行](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Windows 10、Windows 8.1、および Windows 8 への .NET Framework 3.5 のインストール](dotnet-35-windows-10.md)
