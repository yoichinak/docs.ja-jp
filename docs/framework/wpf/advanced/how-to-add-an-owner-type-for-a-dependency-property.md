---
title: '方法: 依存関係プロパティの所有者の種類を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401133"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>方法: 依存関係プロパティの所有者の種類を追加する
この例では、別の型に登録されている依存関係プロパティの所有者としてクラスを追加する方法を示します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] これ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]により、リーダーとプロパティシステムは、クラスをプロパティの追加所有者として認識できるようになります。 所有者として追加すると、追加クラスで型固有のメタデータを提供できるようになります。  
  
 次の例では`StateProperty` 、は`MyStateControl`クラスによって登録されるプロパティです。 クラス`UnrelatedStateControl`は、 <xref:System.Windows.DependencyProperty.AddOwner%2A>メソッドを使用して、 `StateProperty`それ自体をの所有者として追加します。特に、追加する型に存在する依存関係プロパティの新しいメタデータを許可する署名を使用します。 「[依存関係プロパティの実装](how-to-implement-a-dependency-property.md)」の例に示すように、プロパティの共通言語ランタイム (CLR) アクセサーを提供する必要があることに注意してください。また、所有者として追加されるクラスの依存関係プロパティの識別子を再公開することもできます。  
  
 ラッパーがない場合でも、依存関係プロパティはまたは<xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>を使用したプログラムによるアクセスの観点から機能します。 ただし、通常は、このプロパティシステムの動作を CLR プロパティラッパーと並列にする必要があります。 ラッパーを使用すると、依存関係プロパティをプログラムで設定しやすくなり、プロパティを属性と[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]して設定できるようになります。  
  
 既定のメタデータをオーバーライドする方法については、「[依存関係プロパティのメタデータのオーバーライド](how-to-override-metadata-for-a-dependency-property.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>関連項目

- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
