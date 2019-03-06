---
title: '方法: ControlTemplate によって生成された要素を検索します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 9a6609d70a6b863f16533aac81ffce4daf171bcf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364503"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>方法: ControlTemplate によって生成された要素を検索します。
この例によって生成される要素を検索する方法を示しています、<xref:System.Windows.Controls.ControlTemplate>します。  
  
## <a name="example"></a>例  
 次の例は、単純なを作成するスタイル<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>クラス。  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 テンプレートが適用された後は、テンプレート内の要素を検索を呼び出すことができます、<xref:System.Windows.FrameworkTemplate.FindName%2A>のメソッド、<xref:System.Windows.Controls.Control.Template%2A>します。 次の例の実際の幅の値を示すメッセージ ボックスの作成、<xref:System.Windows.Controls.Grid>コントロール テンプレート内で。  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>関連項目
- [DataTemplate によって生成された要素を検索する](../data/how-to-find-datatemplate-generated-elements.md)
- [スタイルとテンプレート](styling-and-templating.md)
- [WPF XAML 名前スコープ](../advanced/wpf-xaml-namescopes.md)
- [WPF のツリー](../advanced/trees-in-wpf.md)
