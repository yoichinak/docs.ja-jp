---
title: 遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 6b78dfed1d615ba865f136365eac1c9c131ed5a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661948"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
オブジェクトは、[Object データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)として宣言された変数に代入されます。  
  
 変数を `Object` として宣言した場合、コンパイラでは*遅延バインディング*を実行する必要があり、これによって実行時に余分な処理が発生します。 また、アプリケーションで実行時エラーが発生する可能性があります。 たとえば、`Object` 変数に <xref:System.Windows.Forms.Form> を代入し、<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> プロパティにアクセスしようとすると、<xref:System.Windows.Forms.Form> クラスが `NameTable` プロパティを公開しないため、ランタイムで <xref:System.MemberAccessException> がスローされます。  
  
 変数を特定の型として宣言する場合、コンパイラではコンパイル時に*事前バインディング*を実行できます。 これにより、パフォーマンスが向上し、特定の型のメンバーへのアクセスが制御され、コードが読みやすくなります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC42017  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 可能であれば、変数を特定の型として宣言します。  
  
## <a name="see-also"></a>関連項目

- [事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
