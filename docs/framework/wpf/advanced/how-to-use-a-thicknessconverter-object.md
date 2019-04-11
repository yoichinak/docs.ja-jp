---
title: '方法: ThicknessConverter オブジェクトを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: ebfb8642a01f6d602f4e5ffa58fde6a8ee0b4e1f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075952"
---
# <a name="how-to-use-a-thicknessconverter-object"></a>方法: ThicknessConverter オブジェクトを使用する
## <a name="example"></a>例  
 この例のインスタンスを作成する方法を示しています。<xref:System.Windows.ThicknessConverter>境界線の太さを変更するとします。  
  
 例では、呼び出されるカスタム メソッドを定義します`changeThickness`; このメソッドは、最初の内容を変換、<xref:System.Windows.Controls.ListBoxItem>個別で定義されている、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]のインスタンスへのファイル<xref:System.Windows.Thickness>、後に、コンテンツに変換します、 <xref:System.String>。 このメソッドは、<xref:System.Windows.Controls.ListBoxItem>に、<xref:System.Windows.ThicknessConverter>オブジェクトで、変換、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Windows.Thickness>。 この値の値として戻されますが、<xref:System.Windows.Controls.Border.BorderThickness%2A>のプロパティ、<xref:System.Windows.Controls.Border>します。  
  
 この例は実行できません。  
  
 [!code-csharp[ThicknessConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- [方法: Margin プロパティを変更します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))
- [方法: ListBoxItem を新しいデータ型に変換します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))
- [パネルの概要](../controls/panels-overview.md)
