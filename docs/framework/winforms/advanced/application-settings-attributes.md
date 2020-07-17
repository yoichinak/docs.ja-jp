---
title: アプリケーション設定の属性
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: b38ed931cab3a333a56dd027d5843b1c8f00dcb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916679"
---
# <a name="application-settings-attributes"></a>アプリケーション設定の属性
アプリケーション設定のアーキテクチャには、アプリケーション設定のラッパークラスまたはその個々のプロパティに適用できる多くの属性が用意されています。 これらの属性は、アプリケーション設定インフラストラクチャ (多くの場合、設定プロバイダー) によって実行時に検査され、カスタムラッパーの要件に合わせて機能を調整します。  
  
 次の表に、アプリケーション設定のラッパークラス、このクラスの個々のプロパティ、またはその両方に適用できる属性を示します。 定義上、1つのスコープ属性 (**system.configuration.userscopedsettingattribute>** または**ApplicationScopedSettingAttribute**) のみを、各設定プロパティに適用する必要があります。  
  
> [!NOTE]
> <xref:System.Configuration.SettingsProvider>クラスから派生したカスタム設定プロバイダーは、次の3つの属性を認識するためにのみ必要です。**ApplicationScopedSettingAttribute**、 **System.configuration.userscopedsettingattribute>** 、および**defaultsettingvalueattribute**。  
  
|属性|ターゲット|説明|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|両方|永続化に使用する設定プロバイダーの短い名前を指定します。<br /><br /> この属性が指定されていない場合、 <xref:System.Configuration.LocalFileSettingsProvider>既定のプロバイダーであるが想定されます。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|両方|プロパティをユーザースコープのアプリケーション設定として定義します。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|両方|アプリケーションスコープのアプリケーション設定としてプロパティを定義します。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|プロパティ|プロバイダーによって、このプロパティのハードコーディングされた既定値に逆シリアル化できる文字列を指定します。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider>はこの属性を必要とせず、既に永続化されている値がある場合に、この属性によって提供される値をオーバーライドします。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|プロパティ|主にランタイムおよびデザイン時ツールによって使用される、個々の設定についての説明のテストを提供します。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|クラス|設定グループの明示的な名前を提供します。 この属性が指定され<xref:System.Configuration.ApplicationSettingsBase>ていない場合、はラッパークラス名を使用します。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|クラス|設定グループについての説明のテストを提供します。主に実行時およびデザイン時のツールによって使用されます。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|両方|設定グループまたはプロパティに提供する必要のある、0個以上の管理サービスを指定します。 使用可能なサービスは、 <xref:System.Configuration.SettingsManageability>列挙体によって記述されます。|  
|<xref:System.Configuration.SpecialSettingAttribute>|プロパティ|設定が、設定プロバイダーによって特別に処理されることを示す、接続文字列などの特別な事前定義されたカテゴリに属していることを示します。 この属性の定義済みのカテゴリは、 <xref:System.Configuration.SpecialSetting>列挙体によって定義されます。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|両方|設定グループまたはプロパティに対して推奨されるシリアル化メカニズムを指定します。 使用できるシリアル化機構は、 <xref:System.Configuration.SettingsSerializeAs>列挙体によって定義されます。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|プロパティ|設定プロバイダーが、マークされたプロパティのすべてのアプリケーションアップグレード機能を無効にする必要があることを指定します。|  
  
 *クラス*は、属性をアプリケーション設定ラッパークラスにのみ適用できることを示します。 *プロパティ*は、属性を適用できるのは設定プロパティのみであることを示します。 *どちら*の場合も、属性をどちらのレベルでも適用できることを示します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [アプリケーション設定アーキテクチャ](application-settings-architecture.md)
- [方法: アプリケーション設定の作成](how-to-create-application-settings.md)
