---
title: XAML における xml:space の処理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: d15bab1ad9234959048fa7b7c3fa2bbbeca5fe6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193318"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML における xml:space の処理
`xml:space`属性は、オブジェクト要素内で大量の空白処理動作を宣言する XML で定義された属性。 この動作は、要素内に含まれるすべてのコンテンツ (内部テキ スト) に関連する場所`xml:space`が宣言され、スコープも子要素にします。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- または -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Remarks  
 定義、`xml:space`はその 2 つの値を含む XAML 内の属性に由来`xml:space`W3C XML 仕様で「特別な属性」として定義されています。  
  
 既定値、`xml:space`属性は、リテラル値`"default"`します。 値の`"default"`、または`xml:space`が反映されていません、すべてのトピックで定義されているの重要な空白文字の解析動作が既定の処理、[空白 XAML 処理](whitespace-processing-in-xaml.md)。  
  
 オブジェクト要素のコンテンツ内の空白を保持するために次のように指定します。`xml:space="preserve"`に、そのオブジェクト。  
  
 ほとんどの解釈、`xml:space`属性の効果と属性の値が子要素にスコープ設定されます。  
  
 空白文字で XAML 処理の詳細については、次を参照してください。[空白 XAML 処理](whitespace-processing-in-xaml.md)します。  
  
## <a name="see-also"></a>関連項目

- [空白 XAML での処理](whitespace-processing-in-xaml.md)
- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
