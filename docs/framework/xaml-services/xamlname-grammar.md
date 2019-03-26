---
title: XamlName の文法
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 642ca16142bdfe78a40ddf4e6a3a79ce6a8a4985
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58031609"
---
# <a name="xamlname-grammar"></a>XamlName の文法
XamlName の文法では、便宜上、ここに再掲は、XAML 言語仕様 [MS-XAML] で定義されている特定の文法です。  
  
## <a name="from-the-xaml-specification"></a>XAML 仕様から  
 [MS XAML] の仕様には、型とプロパティに使用される法的のシンボリック識別子のセットを識別するために XamlName の文法が定義されています。  
  
 次の文法に従う必要があります XamlName 型の値を文字列には。  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Unicode 文字データベースで定義されている次の一般的なカテゴリ値を想定しています  
  
```  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 XAML は、2 番目の文法、DottedXamlName、プロパティに使用されるを定義し、イベントの修飾参照、およびものメンバーをアタッチします。 詳細については、<xref:System.Windows.DependencyProperty>と[XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)を参照してください。  
  
 次の文法に従う必要があります DottedXamlName 型の値を文字列には。  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Remarks  
 完全な仕様では、[ \[MS XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)を参照してください。
