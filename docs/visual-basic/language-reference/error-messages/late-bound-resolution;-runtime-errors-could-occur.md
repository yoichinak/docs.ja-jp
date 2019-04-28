---
title: 遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 4fe79c74b6ff634223a4f10d8c5dc54bb77571cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921148"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
オブジェクトが宣言する変数に割り当てられている、 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)します。  
  
 として変数を宣言するときに`Object`、コンパイラを実行する必要があります*遅延バインディング*、実行時に余分な処理を停止します。 また、アプリケーションで実行時エラーが発生する可能性があります。 割り当てる場合など、<xref:System.Windows.Forms.Form>を`Object`変数にアクセスしようと、<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType>プロパティ、ランタイムは、スロー、<xref:System.MemberAccessException>ため、<xref:System.Windows.Forms.Form>クラスを公開しません、`NameTable`プロパティ。  
  
 特定の型の変数を宣言する場合、コンパイラを実行できます*事前バインディング*コンパイル時にします。 これは、結果、パフォーマンスの向上、特定の型のメンバーと、コードの読みやすさへのアクセスを制御します。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC42017  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 可能であれば、特定の型の変数を宣言します。  
  
## <a name="see-also"></a>関連項目

- [事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
