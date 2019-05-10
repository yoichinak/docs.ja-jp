---
title: <proceduresignature1> オーバー ロードするため、CLS 準拠<proceduresignature2>これが異なる配列パラメーター型の配列または配列パラメーター型のランクのみ
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 9006e12838581a98c7e7945278c7d767a3074259
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661797"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > は、オーバー ロードするため、CLS 準拠\<proceduresignature2 > これが異なる配列パラメーター型の配列または配列パラメーター型のランクのみ
プロシージャまたはプロパティがマーク`<CLSCompliant(True)>`と別のプロシージャまたはプロパティのオーバーライド、パラメーター リストの唯一の違いは、ジャグ配列の入れ子レベルまたは配列のランク。  
  
 次の宣言では、2 番目と 3 番目の宣言は、このエラーを生成します。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 2 番目の宣言元の 1 次元のパラメーターを変更する`arrayParam`配列の配列にします。 3 番目の宣言の変更`arrayParam`2 次元配列 (ランク 2) にします。 Visual Basic でこれらの変更のいずれかによってのみ異なるオーバー ロードは、中にこのようなオーバー ロードが準拠していない、 [Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS)。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC40035  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- CLS 準拠が必要な場合は、このヘルプ ページに示された変更のみよりも多くの方法で互いに異なる、オーバー ロードを定義します。  
  
- このヘルプで示された変更によってのみページ オーバー ロードとは異なることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>その定義からとしてマークまたは`<CLSCompliant(False)>`します。  
  
## <a name="see-also"></a>関連項目

- [プロシージャのオーバーロード](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
