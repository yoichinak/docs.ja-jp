---
title: UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加
description: .NET で Microsoft UI オートメーションを使用して、コンテンツを単一行のテキストボックスに追加する方法の例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 4136d460de7091a515580cade16f06e54699727a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166914"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、を使用して [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 1 行のテキストボックスにテキストを挿入する方法を示すコード例を示します。 複数行およびリッチテキストコントロールに対して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、を適用できない代替の方法が用意されています。 比較のために、この例では、Win32 メソッドを使用して同じ結果を実現する方法も示しています。  
  
## <a name="example"></a>例  
 次の例では、対象アプリケーションのテキストコントロールのシーケンスをステップ実行します。 各テキストコントロールは、 <xref:System.Windows.Automation.ValuePattern> メソッドを使用してオブジェクトを取得できるかどうかをテストし <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> ます。 テキストコントロールでがサポートされている場合、メソッドを使用して、 <xref:System.Windows.Automation.ValuePattern> <xref:System.Windows.Automation.ValuePattern.SetValue%2A> ユーザー定義の文字列をテキストコントロールに挿入します。 それ以外の場合は、 <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> メソッドが使用されます。  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>関連項目

- [TextPattern の挿入テキストのサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
