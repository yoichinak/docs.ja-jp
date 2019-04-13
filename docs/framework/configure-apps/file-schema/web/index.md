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
ms.openlocfilehash: 1f0241b65c915dd5703ceea97dd5b07f88832003
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113062"
---
# <a name="web-settings-schema"></a>Web 設定スキーマ
Web 設定は、CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。 これらの設定は、ASP.NET アプリケーションの Web.config ファイルで指定されているアプリケーション ドメインの種類の設定とは異なります。  
  
 Web 設定は、.NET Framework のバージョンのインストール フォルダーに配置された Aspnet.config ファイルに格納されます。 たとえば、[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] の Aspnet.config ファイルは次のフォルダーにあります。  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Web 設定は、machine.config ファイル、ルート、Web.config ファイル、アプリケーション レベルの Web.config ファイルなどの他の構成ファイルでは使用されません。  
  
 [\<configuration > 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.web > 要素 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool > 要素 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET ホスト層が使用する情報が含まれています。|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。|  
  
## <a name="see-also"></a>関連項目

- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
