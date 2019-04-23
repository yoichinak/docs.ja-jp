---
title: アプリケーションの構成
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 94bf5f4bbee8bb8bb462c4bf91be75d1627ec567
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087171"
---
# <a name="configuring-your-application"></a>アプリケーションの構成
Windows Communication Foundation (WCF) は、.NET 構成システムを使用し、コンピューターとアプリケーションの両方のスコープでサービスを構成することができます。  
  
 WCF によって定義された構成設定にある、`<system.serviceModel>`セクション グループ。 WCF サービスを構成する方法の詳細については、次のトピックを参照してください。  
  
-   [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 アプリケーション定義の構成設定は、`<appSettings>` セクション グループで定義されています。 .NET 構成ファイル内のアプリケーション設定の詳細については、次を参照してください。 [ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159)します。  
  
## <a name="using-the-configuration-editor"></a>構成エディターの使用  
 WCF[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)管理者および開発者を作成およびグラフィカル ユーザー インターフェイスを使用して WCF サービスの構成設定を変更します。 このツールでは、XML 構成ファイルを直接編集することがなく WCF バインディング、動作、サービス、および診断の設定を管理できます。  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Visual Studio の構成ファイルの編集  
 Visual Studio での WCF サービス プロジェクトの構成ファイルを編集するには、右クリックで**ソリューション エクスプ ローラー**を選択し、 **Edit WCF Config**コンテキスト メニュー項目。 これにより、起動、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)します。  
  
> [!NOTE]
>  右クリックして Visual Studio での WCF Web サービス プロジェクトの構成ファイルを編集する場合**ソリューション エクスプ ローラー**、注意、 **Edit WCF Config**コンテキスト メニュー項目がありません。 この問題を回避するには、をクリックして、**ツール**] メニューの [選択**WCF Service Config Editor**します。 その後、構成ファイルを右クリックし、使用して、、 **Edit WCF Config**コンテキスト メニュー項目。  
  
## <a name="see-also"></a>関連項目

- [構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
