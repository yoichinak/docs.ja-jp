---
title: UI オートメーション プロバイダーからのイベントの発生
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 3deb4c6716d83af4b05e15b5b8a4b89e28317406
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138698"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>UI オートメーション プロバイダーからのイベントの発生
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックには、UI オートメーション プロバイダーからイベントを発生させる方法を示すコード例が記載されています。  
  
## <a name="example"></a>例  
 次の例では、カスタム ボタン コントロールの実装で [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントが発生します。 実装により、UI オートメーション クライアント アプリケーションがボタンのクリックをシミュレートできるようになります。  
  
 不要な処理を回避するために、例では <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> をチェックして、イベントが発生するかどうかを確認しています。  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション プロバイダーの概要](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
