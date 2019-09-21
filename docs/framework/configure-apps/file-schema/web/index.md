---
title: Web 設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: d53d3a105203addfacb1c982e0960bd12996f571
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941422"
---
# <a name="web-settings-schema"></a>Web 設定スキーマ
Web 設定は、CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。 これらの設定は、ASP.NET アプリケーションの Web.config ファイルで指定されているアプリケーション ドメインの種類の設定とは異なります。  
  
 Web 設定は、.NET Framework のバージョンのインストール フォルダーに配置された Aspnet.config ファイルに格納されます。 たとえば、.NET Framework 2.0 の Aspnet .config ファイルは、次のフォルダーにあります。  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Web 設定は、machine.config ファイル、ルート、Web.config ファイル、アプリケーション レベルの Web.config ファイルなどの他の構成ファイルでは使用されません。  
  
 [\<configuration> 要素](../configuration-element.md)  
  
 [\<system.web> 要素 (Web 設定)](system-web-element-web-settings.md)  
  
 [\<applicationPool> 要素 (Web 設定)](applicationpool-element-web-settings.md)  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.web >](system-web-element-web-settings.md)|ASP.NET ホスト層が使用する情報が含まれています。|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。|  
  
## <a name="see-also"></a>関連項目

- [構成ファイル スキーマ](../index.md)
