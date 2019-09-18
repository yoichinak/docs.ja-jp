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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053704"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 組み込み XAML 型
XAML 運用環境内での XML データアイランドの配置を有効にします。 内`x:XData`の XML 要素は、動作する既定の xaml 名前空間またはその他の xaml 名前空間の一部であるかのように、xaml プロセッサによって処理されないようにする必要があります。 `x:XData`任意の整形式の XML を含めることができます。  
  
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
|`elementDataRoot`|囲まれたデータアイランドの単一のルート要素。 最終的なコンシューマーの多くは、1つのルートを持たない XML は無効と見なされます。 特に、 `x:XData`が WPF の xml データソースである場合、またはデータバインディングに xml ソースを使用するその他の多くのテクノロジの場合は、単一のルートが必要です。|  
|`[elementData]`|任意。 XML データを表す XML です。 要素データとして任意の数の要素を含めることができ、入れ子になった要素を他の要素に含めることができます。ただし、XML の一般的な規則が適用されます。|  
  
## <a name="remarks"></a>Remarks  
 `x:XData`オブジェクト内の XML 要素は、データ内の格納されている XMLDOM のすべての可能な名前空間とプレフィックスを再宣言できます。  
  
 XML データと`x:XData`組み込み xaml 型へのプログラムによるアクセスは、 <xref:System.Windows.Markup.XData> .NET Framework xaml サービスでクラスを使用して行うことができます。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 オブジェクトは<xref:System.Windows.Data.XmlDataProvider>、主にの子オブジェクトとして使用されるか、または<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>プロパティの子オブジェクトとして使用されます (XAML では、これは通常、プロパティ要素構文で表されます)。 `x:XData`  
  
 データは、通常、データアイランド内の基本 XML 名前空間を新しい既定の XML 名前空間 (空の文字列に設定) に再定義する必要があります。 データの参照とバインドに使用される<xref:System.Windows.Data.Binding.XPath%2A>式ではプレフィックスが含まれないため、単純なデータアイランドではこの方法が最も簡単です。 より複雑なデータアイランドでは、データに複数のプレフィックスを定義し、ルートで XML 名前空間に特定のプレフィックスを使用する場合があります。 この場合、すべて<xref:System.Windows.Data.Binding.XPath%2A>の式参照には、適切な名前空間にマップされたプレフィックスが含まれている必要があります。 詳しくは、「 [データ バインディングの概要](../wpf/data/data-binding-overview.md)」をご覧ください。  
  
 技術的に`x:XData`は、型<xref:System.Xml.Serialization.IXmlSerializable>の任意のプロパティのコンテンツとして使用できます。 ただし、 <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>は唯一の実装です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.XmlDataProvider>
- [データ バインディングの概要](../wpf/data/data-binding-overview.md)
- [バインドのマークアップ拡張機能](../wpf/advanced/binding-markup-extension.md)
