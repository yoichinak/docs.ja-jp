---
title: UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932653"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 このトピックでは、を使用[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]して1行のテキストボックスにテキストを挿入する方法を示すコード例を示します。 複数行およびリッチテキストコントロール[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に対しては、を適用できない代替の方法が用意されています。 比較のために、この例では、Win32 メソッドを使用して同じ結果を実現する方法も示しています。  
  
## <a name="example"></a>例  
 次の例では、対象アプリケーションのテキストコントロールのシーケンスをステップ実行します。 各テキストコントロールは、 <xref:System.Windows.Automation.ValuePattern> <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>メソッドを使用してオブジェクトを取得できるかどうかをテストします。 テキストコントロールでがサポート<xref:System.Windows.Automation.ValuePattern>されている場合<xref:System.Windows.Automation.ValuePattern.SetValue%2A> 、メソッドを使用して、ユーザー定義の文字列をテキストコントロールに挿入します。 それ以外の<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>場合は、メソッドが使用されます。  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>関連項目

- [TextPattern の挿入テキストのサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
