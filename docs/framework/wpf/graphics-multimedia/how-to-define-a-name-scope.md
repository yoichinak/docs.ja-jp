---
title: '方法: 名前のスコープを定義する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: 6afb59550d774109c62c283905495c76b0834b3d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370372"
---
# <a name="how-to-define-a-name-scope"></a>方法: 名前のスコープを定義する
使用してアニメーション化<xref:System.Windows.Media.Animation.Storyboard>コードで作成する必要があります、<xref:System.Windows.NameScope>し、その名前のスコープを所有している要素にターゲット オブジェクトの名前を登録します。 次の例では、<xref:System.Windows.NameScope>が作成されます`myMainPanel`します。 2 つのボタン`button1`と`button2`パネル、および登録名に追加されます。 複数のアニメーションと<xref:System.Windows.Media.Animation.Storyboard>が作成されます。 ストーリー ボードの<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>アニメーションを開始するメソッドを使用します。  
  
 `button1`、 `button2`、および`myMainPanel`すべて同じ名前のスコープを共有、それらのいずれかで使用できる、 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>アニメーションを開始するメソッド。  
  
## <a name="example"></a>例  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>関連項目
- [ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)
- [アニメーションの概要](animation-overview.md)
