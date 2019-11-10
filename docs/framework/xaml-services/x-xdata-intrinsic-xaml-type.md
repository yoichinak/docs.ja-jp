---
title: x:XData 組み込み XAML 型
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459905"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 組み込み XAML 型
XAML 運用環境内での XML データアイランドの配置を有効にします。 `x:XData` 内の XML 要素は、動作する既定の XAML 名前空間またはその他の XAML 名前空間の一部であるかのように、XAML プロセッサによって処理されないようにする必要があります。 `x:XData` には、任意の整形式の XML を含めることができます。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`elementDataRoot`|囲まれたデータアイランドの単一のルート要素。 最終的なコンシューマーの多くは、1つのルートを持たない XML は無効と見なされます。 特に、`x:XData` が WPF の XML データソースである場合、またはデータバインディングに XML ソースを使用するその他の多くのテクノロジの場合は、単一のルートが必要です。|  
|`[elementData]`|省略可能です。 XML データを表す XML です。 要素データとして任意の数の要素を含めることができ、入れ子になった要素を他の要素に含めることができます。ただし、XML の一般的な規則が適用されます。|  
  
## <a name="remarks"></a>Remarks  
 `x:XData` オブジェクト内の XML 要素は、データ内のすべての可能な名前空間と、それを含む XMLDOM のプレフィックスを再宣言できます。  
  
 XML データと `x:XData` 組み込み XAML 型へのプログラムによるアクセスは、.NET Framework XAML サービスで <xref:System.Windows.Markup.XData> クラスを使用して行うことができます。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 `x:XData` オブジェクトは、主に <xref:System.Windows.Data.XmlDataProvider>の子オブジェクトとして使用されるか、または <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> プロパティの子オブジェクトとして使用されます (XAML では通常、これはプロパティ要素の構文で表されます)。  
  
 データは、通常、データアイランド内の基本 XML 名前空間を新しい既定の XML 名前空間 (空の文字列に設定) に再定義する必要があります。 データを参照してバインドするために使用される <xref:System.Windows.Data.Binding.XPath%2A> 式はプレフィックスを含めることができないため、単純なデータアイランドではこの方法が最も簡単です。 より複雑なデータアイランドでは、データに複数のプレフィックスを定義し、ルートで XML 名前空間に特定のプレフィックスを使用する場合があります。 この場合、すべての <xref:System.Windows.Data.Binding.XPath%2A> 式参照には、適切な名前空間にマップされたプレフィックスが含まれている必要があります。 詳しくは、「[データ バインディングの概要](../../desktop-wpf/data/data-binding-overview.md)」をご覧ください。  
  
 技術的には、`x:XData` <xref:System.Xml.Serialization.IXmlSerializable>型のプロパティのコンテンツとして使用できます。 ただし、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> は唯一の実装です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.XmlDataProvider>
- [データ バインディングの概要](../../desktop-wpf/data/data-binding-overview.md)
- [バインドのマークアップ拡張機能](../wpf/advanced/binding-markup-extension.md)
