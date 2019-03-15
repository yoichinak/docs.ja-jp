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
ms.openlocfilehash: 68468c3c10fd884cf5fb92160e3cde41dbf7d529
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58030266"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 組み込み XAML 型
XAML の運用環境での XML データ アイランドの配置を有効にします。 内の XML 要素`x:XData`が動作する既定の XAML 名前空間の一部かその他の XAML 名前空間かのように XAML プロセッサで扱うことはできません。 `x:XData` 任意の整形式 XML を含めることができます。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`elementDataRoot`|囲まれたデータ アイランドの単一のルート要素。 ほとんどの最終的なコンシューマーの単一のルートがない XML が無効と見なされます。 具体的には、単一のルートは、必要な場合、 `x:XData` WPF のデータ バインディングの XML ソースを使用する他の多くのテクノロジとして XML データ ソースを対象としています。|  
|`[elementData]`|任意。 XML データを表す XML。 要素のデータとして格納できる要素の任意の数と、入れ子になった要素を他の要素に含めることができます。ただし、XML の一般的な規則が適用されます。|  
  
## <a name="remarks"></a>Remarks  
 内の XML 要素、`x:XData`オブジェクトすべての可能な名前空間と、データ内に含む XMLDOM のプレフィックスを再宣言できます。  
  
 XML データにプログラムでアクセスし、`x:XData`組み込み XAML 型から .NET Framework XAML サービスでは、<xref:System.Windows.Markup.XData>クラス。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 `x:XData`オブジェクトの子オブジェクトとして主に使用、 <xref:System.Windows.Data.XmlDataProvider>、または代わりの子オブジェクトとして、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>プロパティ (で XAML、これは通常表現プロパティ要素構文で)。  
  
 データには、ベースの XML 名前空間を新しい既定の XML 名前空間 (空の文字列に設定) にデータ アイランド内で通常再定義しなければなりません。 これは、単純なデータ諸島ための最も簡単な<xref:System.Windows.Data.Binding.XPath%2A>参照およびデータにバインドするために使用する式は、プレフィックスを含めることを避けることができます。 複雑なデータ アイランドは、データの複数のプレフィックスを定義して、ルートにある XML 名前空間の特定のプレフィックスを使用して、可能性があります。 この場合、すべて<xref:System.Windows.Data.Binding.XPath%2A>式の参照は、適切な名前空間マッピング プレフィックスを含める必要があります。 詳しくは、「 [データ バインディングの概要](../wpf/data/data-binding-overview.md)」をご覧ください。  
  
 技術的には、`x:XData`型のプロパティの内容として使用できる<xref:System.Xml.Serialization.IXmlSerializable>します。 ただし、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>のみ、著名な実装です。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Data.XmlDataProvider>
- [データ バインディングの概要](../wpf/data/data-binding-overview.md)
- [バインドのマークアップ拡張機能](../wpf/advanced/binding-markup-extension.md)
