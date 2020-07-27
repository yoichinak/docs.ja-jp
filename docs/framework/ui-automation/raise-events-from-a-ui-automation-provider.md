---
title: UI オートメーション プロバイダーからのイベントの発生
description: UI オートメーションプロバイダーからイベントを発生させる方法を示す例を参照してください。 このメソッドは、カスタムボタンコントロールの実装で UI オートメーションイベントを発生させます。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 75af4d05172e2417d44f76beab486de5eb3a4ba7
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168106"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>UI オートメーション プロバイダーからのイベントの発生
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックには、UI オートメーション プロバイダーからイベントを発生させる方法を示すコード例が記載されています。  
  
## <a name="example"></a>例  
 次の例では、カスタム ボタン コントロールの実装で [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントが発生します。 実装により、UI オートメーション クライアント アプリケーションがボタンのクリックをシミュレートできるようになります。  
  
 不要な処理を回避するために、例では <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> をチェックして、イベントが発生するかどうかを確認しています。  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション プロバイダーの概要](ui-automation-providers-overview.md)
