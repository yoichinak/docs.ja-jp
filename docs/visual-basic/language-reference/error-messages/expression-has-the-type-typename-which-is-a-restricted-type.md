---
title: 式は制限がある型 '<typename>' を含んでいるため、'Object' または 'ValueType' から継承されたメンバーにアクセスするのに使用できません。
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 6d2edadc323994f7f25394321fb1aff18f7154c5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824274"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>式の型 '\<typename >' は制限付きの型と 'Object' または 'ValueType' から継承されたメンバーのアクセスに使用することはできません
式では、共通言語ランタイム (CLR) でボックス化できない型に評価が、ボックス化を必要とするメンバーにアクセスします。  
  
 *ボックス化* とは、型を `Object` (場合によっては <xref:System.ValueType>) に変換するために不可欠な処理です。 共通言語ランタイムでは、特定の構造体の型をたとえばボックスことはできません<xref:System.ArgIterator>、 <xref:System.RuntimeArgumentHandle>、および<xref:System.TypedReference>します。  
  
 この式から継承されたメソッドの呼び出しに制限付きの型を使用しようとしました。<xref:System.Object>または<xref:System.ValueType>、など<xref:System.Object.GetHashCode%2A>または<xref:System.Object.ToString%2A>します。 このメソッドにアクセスするには、Visual Basic はこのエラーが発生する暗黙的なボックス化変換をしようとしました。  
  
 **エラー ID:** BC31393  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  問題の型に評価される式を探します。  
  
2.  継承されたメソッドを呼び出そうとすると、ステートメントの部分を探します<xref:System.Object>または<xref:System.ValueType>します。  
  
3.  メソッドの呼び出しを回避するために、ステートメントを書き直してください。  
  
## <a name="see-also"></a>関連項目

- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
