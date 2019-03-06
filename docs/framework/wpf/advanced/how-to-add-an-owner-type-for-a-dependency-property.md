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
ms.openlocfilehash: 03ffec87c98c88452aa8fde89c64646eaf48a8da
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369592"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>方法: 依存関係プロパティの所有者の種類を追加する
この例では、異なる種類の登録されている依存関係プロパティの所有者としてクラスを追加する方法を示します。 この手順を実行して、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リーダーとプロパティ システムの両方のプロパティの追加の所有者としてクラスを認識することができます。 必要に応じて所有者として追加すると、型固有のメタデータを提供する追加のクラスができます。  
  
 次の例では、`StateProperty`によってプロパティが登録、`MyStateControl`クラス。 クラスは、`UnrelatedStateControl`自体の所有者として追加、`StateProperty`を使用して、<xref:System.Windows.DependencyProperty.AddOwner%2A>メソッド、具体的には、追加の型に存在する依存関係プロパティの新しいメタデータは、署名を使用します。 提供する必要がありますに注意してください[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]に示した例のようなプロパティのアクセサー、[依存関係プロパティを実装して](how-to-implement-a-dependency-property.md)など、追加されるクラスの依存関係プロパティ識別子を再公開所有者。  
  
 ラッパーの依存関係プロパティは機能を使用したプログラムによるアクセスの観点から<xref:System.Windows.DependencyObject.GetValue%2A>または<xref:System.Windows.DependencyObject.SetValue%2A>します。 通常の場合は、このプロパティ システム動作するには、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティ ラッパー。 ラッパーがプログラムで、依存関係プロパティを設定するが容易し、としてのプロパティを設定することを可能[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性。  
  
 既定のメタデータをオーバーライドする方法についてを参照してください。[依存関係プロパティのメタデータをオーバーライド](how-to-override-metadata-for-a-dependency-property.md)します。  
  
## <a name="example"></a>例  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>関連項目
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
