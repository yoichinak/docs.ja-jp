---
title: '方法: 列挙値にバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: df26d2bd08e4691837f739a4e71d3bb1a25bdd00
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377795"
---
# <a name="how-to-bind-to-an-enumeration"></a>方法: 列挙値にバインドする
この例では、列挙型の GetValues メソッドにバインドして列挙型にバインドする方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Controls.ListBox>の一覧を表示します<xref:System.Windows.HorizontalAlignment>データ バインディングの列挙値。 <xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.Button>を変更するようにバインドされて、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティの値、<xref:System.Windows.Controls.Button>で値を選択して、<xref:System.Windows.Controls.ListBox>します。  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>関連項目
- [メソッドにバインドする](how-to-bind-to-a-method.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
