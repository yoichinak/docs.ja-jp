---
title: '方法: カーソルの種類を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: e62658f4c4249c93bd24dffd3878dd2ec2b75029
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371153"
---
# <a name="how-to-change-the-cursor-type"></a>方法: カーソルの種類を変更する
この例では、変更、<xref:System.Windows.Input.Cursor>とアプリケーションの特定の要素をマウス ポインターの。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コード ファイル。  
  
## <a name="example"></a>例  
 ユーザー インターフェイスを作成するから構成される、<xref:System.Windows.Controls.ComboBox>目的を選択する<xref:System.Windows.Input.Cursor>、1 組の<xref:System.Windows.Controls.RadioButton>カーソルの変更は 1 つの要素のみに適用されますか、アプリケーション全体に適用されますかを判断するオブジェクトと<xref:System.Windows.Controls.Border>これは、新しいカーソルに適用される要素です。  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 次のコードを作成、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>で、カーソルの種類が変更されたときに呼び出されるイベント ハンドラー、<xref:System.Windows.Controls.ComboBox>します。  Switch ステートメントのセットとカーソルの名前でフィルター処理、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティを<xref:System.Windows.Controls.Border>名前は*DisplayArea*します。  
  
 カーソルの変更は、"全体 Application"に設定されている場合、<xref:System.Windows.Input.Mouse.OverrideCursor%2A>プロパティに設定されて、<xref:System.Windows.FrameworkElement.Cursor%2A>のプロパティ、<xref:System.Windows.Controls.Border>コントロール。  これにより、アプリケーション全体を変更するカーソル。  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>関連項目
- [入力の概要](input-overview.md)
