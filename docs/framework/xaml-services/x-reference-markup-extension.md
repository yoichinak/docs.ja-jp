---
title: x:Reference のマークアップ拡張機能
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938880"
---
# <a name="xreference-markup-extension"></a>x:Reference のマークアップ拡張機能
XAML マークアップで他の場所で宣言されているインスタンスを参照します。 参照が指す要素の`x:Name`します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`instancexName`|`x:Name`値 (またはの値、 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-プロパティを識別) の参照先のインスタンス。|  
  
## <a name="remarks"></a>Remarks  
 `x:Reference` WPF などの特定のフレームワークで実装された場合は要素の参照の概念の XAML 言語レベルのサポートを提供します。  
  
## <a name="xreference-and-wpf"></a>X:reference と WPF  
 WPF および XAML 2006 では、要素の参照は、フレームワーク レベルの機能のによってアドレス指定<xref:System.Windows.Data.Binding.ElementName%2A>バインドします。 ほとんどの WPF アプリケーションとシナリオでは、<xref:System.Windows.Data.Binding.ElementName%2A>引き続きバインドを使用する必要があります。 この一般的なガイダンスの例外には可能性がありますがあるデータ コンテキスト、またはその他のスコープの考慮事項は実用的でないデータ バインディングを構成する場合、およびマークアップのコンパイルが含まれていない場合、ケースが含まれます。  
  
 `x:Reference` コンストラクトは、XAML 2009 で定義されます。 WPF では XAML 2009 の機能を使用できますが、WPF マークアップ コンパイルされていない XAML に限定されます。 マークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 言語のキーワードと機能をサポートしていません。
