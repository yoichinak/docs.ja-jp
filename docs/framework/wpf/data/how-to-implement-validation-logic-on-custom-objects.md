---
title: '方法: カスタム オブジェクトに検証ロジックを実装する'
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: 8520504757e9e9ec9557b84ca2608b4cb99daf62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085923"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>方法: カスタム オブジェクトに検証ロジックを実装する
この例では、カスタム オブジェクトに検証ロジックを実装し、それにバインドする方法を示します。  
  
## <a name="example"></a>例  
 ソース オブジェクトが実装されている場合、ビジネス層の検証ロジックを行うことができます<xref:System.ComponentModel.IDataErrorInfo>を定義する次の例のように、`Person`を実装するオブジェクト<xref:System.ComponentModel.IDataErrorInfo>:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 次の例で、テキスト ボックスのテキスト プロパティにバインド、`Person.Age`バインドが指定されたリソースの宣言で使用可能なされていますが、プロパティ、 `x:Key` `data`します。 <xref:System.Windows.Controls.DataErrorValidationRule>によって発生した検証エラーをチェック、<xref:System.ComponentModel.IDataErrorInfo>実装します。  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 使用する代わりに、代わりに、 <xref:System.Windows.Controls.DataErrorValidationRule>、設定することができます、<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>プロパティを`true`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [バインディングの検証の実装](how-to-implement-binding-validation.md)
- [方法のトピック](data-binding-how-to-topics.md)
