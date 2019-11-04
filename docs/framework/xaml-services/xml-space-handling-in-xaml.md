---
title: XAML における xml:space の処理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458791"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML における xml:space の処理
`xml:space` 属性は、オブジェクト要素内の有意な空白処理動作を宣言する XML 定義の属性です。 この動作は、`xml:space` が宣言されている要素内に含まれるすべてのコンテンツ (内部テキスト) に関連し、子要素にも適用されます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- または  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Remarks  
 XAML の `xml:space` 属性の定義 (2 つの値を含む) は、XML の W3C 仕様による "特殊な属性" として定義されている `xml:space` から派生します。  
  
 `xml:space` 属性の既定値は `"default"`リテラル値です。 `"default"`値の場合、または `xml:space` がまったく示されていない場合は、「 [XAML での空白の処理](whitespace-processing-in-xaml.md)」で定義されているように、有意な空白の解析の動作が既定の処理になります。  
  
 オブジェクト要素のコンテンツ内の空白を保持するには、そのオブジェクト要素の `xml:space="preserve"` を指定します。  
  
 ほとんどの解釈では、`xml:space` 属性の効果と属性の値が子要素にスコープ設定されます。  
  
 XAML での空白の処理の詳細については、「 [xaml での空白の処理](whitespace-processing-in-xaml.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XAML での空白の処理](whitespace-processing-in-xaml.md)
- [XAML の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
