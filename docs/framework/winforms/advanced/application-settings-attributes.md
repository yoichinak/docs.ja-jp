---
title: アプリケーション設定の属性
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: f945d8e6918c271eeb5fdf3cf9c357b1c2bbca66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699728"
---
# <a name="application-settings-attributes"></a>アプリケーション設定の属性
アプリケーション設定アーキテクチャでは、アプリケーション設定ラッパー クラスまたはその個々 のプロパティに適用できる多くの属性を提供します。 これらの属性は、カスタム ラッパーの規定のニーズに合わせて機能を調整するには、実行時に、アプリケーション設定のインフラストラクチャ、多くの場合、具体的には、設定プロバイダーによって調べられます。  
  
 次の表は、アプリケーション設定ラッパー クラス、このクラスの個々 のプロパティ、またはその両方に適用できる属性を一覧表示します。 定義上、単一のスコープ属性のみ-**UserScopedSettingAttribute**または**ApplicationScopedSettingAttribute**— 各設定プロパティに適用する必要があります。  
  
> [!NOTE]
>  派生した、カスタム設定プロバイダー、<xref:System.Configuration.SettingsProvider>クラスでは、次の 3 つの属性の認識にのみ必要です。**ApplicationScopedSettingAttribute**、 **UserScopedSettingAttribute**、および**DefaultSettingValueAttribute**します。  
  
|属性|ターゲット|説明|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|両方|永続化に使用する設定プロバイダーの短い名前を指定します。<br /><br /> この属性が指定されていない場合、既定のプロバイダー<xref:System.Configuration.LocalFileSettingsProvider>と見なされます。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|両方|アプリケーションのユーザー スコープ設定とプロパティを定義します。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|両方|アプリケーション スコープのアプリケーション設定として、プロパティを定義します。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|プロパティ|このプロパティの既定のハード コーディングされた値に、プロバイダーによって逆シリアル化できる文字列を指定します。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> 、この属性は必要ありませんし、この属性が存在する場合、値既に永続化が提供される任意の値がオーバーライドされます。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|プロパティ|実行時およびデザイン時ツールで主に使用される、個々 の設定の説明的なテストを提供します。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|クラス|設定グループの明示的な名前を提供します。 この属性が見つからない場合<xref:System.Configuration.ApplicationSettingsBase>ラッパー クラス名を使用します。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|クラス|実行時およびデザイン時ツール、主に使用する設定グループの説明的なテストを提供します。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|両方|設定グループまたはプロパティに提供される 0 個以上の管理の容易性のサービスを指定します。 使用可能なサービスが説明されている、<xref:System.Configuration.SettingsManageability>列挙体。|  
|<xref:System.Configuration.SpecialSettingAttribute>|プロパティ|設定が、特別な処理の設定プロバイダーで候補を示す接続文字列など、特別な定義済みのカテゴリに属することを示します。 この属性の定義済みのカテゴリがによって定義されている、<xref:System.Configuration.SpecialSetting>列挙体。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|両方|設定グループまたはプロパティの推奨されるシリアル化メカニズムを指定します。 使用可能なシリアル化メカニズムが定義されている、<xref:System.Configuration.SettingsSerializeAs>列挙体。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|プロパティ|設定プロバイダーにマークされたプロパティのすべてのアプリケーション アップグレード機能が無効にする必要がありますを指定します。|  
  
 *クラス*アプリケーション設定ラッパー クラスにのみ、属性を適用できることを示します。 *プロパティ*属性が設定プロパティだけに適用できることを示します。 *どちらも*どちらのレベルに属性を適用できることを示します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [アプリケーション設定アーキテクチャ](application-settings-architecture.md)
- [方法: アプリケーション設定を作成します。](how-to-create-application-settings.md)
