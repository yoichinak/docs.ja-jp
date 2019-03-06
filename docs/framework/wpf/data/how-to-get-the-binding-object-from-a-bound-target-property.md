---
title: '方法: バインドされているターゲット プロパティからのバインディング オブジェクトの取得'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: af18cf3fc155148816690bdd16baa3a2a5515eee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368520"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>方法: バインドされているターゲット プロパティからのバインディング オブジェクトの取得
この例では、データにバインドされているターゲット プロパティからバインディング オブジェクトを取得する方法を示します。  
  
## <a name="example"></a>例  
 取得するには、次を行うことができます、<xref:System.Windows.Data.Binding>オブジェクト。  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  ターゲット オブジェクトの複数のプロパティがデータ バインディングを使用している可能性があるため、バインディングの依存関係プロパティを指定する必要があります。  
  
 また、取得できます、<xref:System.Windows.Data.BindingExpression>しの値を取得し、<xref:System.Windows.Data.BindingExpression.ParentBinding%2A>プロパティ。  
  
 コード例全体については、「[バインディングの検証のサンプル](https://go.microsoft.com/fwlink/?LinkID=159972)」をご覧ください。  
  
> [!NOTE]
>  バインドがある場合、<xref:System.Windows.Data.MultiBinding>を使用して、 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>します。 ある場合、<xref:System.Windows.Data.PriorityBinding>を使用して、 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>します。 ターゲット プロパティを使用してバインドされているかどうかがない場合、 <xref:System.Windows.Data.Binding>、 <xref:System.Windows.Data.MultiBinding>、または<xref:System.Windows.Data.PriorityBinding>、使用することができます<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>します。  
  
## <a name="see-also"></a>関連項目
- [コードでバインディングを作成する](how-to-create-a-binding-in-code.md)
- [方法トピック](data-binding-how-to-topics.md)
