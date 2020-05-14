---
title: 式は制限がある型 '<typename>' を含んでいるため、'Object' または 'ValueType' から継承されたメンバーにアクセスするのに使用できません。
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 017a2458562068727674bd3fd9cda8c33d989e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803169"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>式は制限がある型 '\<typename>' を含んでいるため、'Object' または 'ValueType' から継承されたメンバーにアクセスするのに使用できません
式が共通言語ランタイム (CLR) でボックス化できない型に評価されますが、ボックス化が必要なメンバーにアクセスします。  
  
 *ボックス化* とは、型を `Object` (場合によっては <xref:System.ValueType>) に変換するために不可欠な処理です。 共通言語ランタイムは、<xref:System.ArgIterator>、<xref:System.RuntimeArgumentHandle>、<xref:System.TypedReference> などの特定の構造体型をボックス化できません。  
  
 この式は、制限がある型を使用して、<xref:System.Object> または <xref:System.ValueType> から継承されたメソッド (<xref:System.Object.GetHashCode%2A> や <xref:System.Object.ToString%2A> など) の呼び出しを試みます。 このメソッドにアクセスするために、Visual Basic は、このエラーの原因となる暗黙的なボックス化変換を試行しました。  
  
 **エラー ID:** BC31393  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 問題の型に評価される式を探します。  
  
2. <xref:System.Object> または <xref:System.ValueType> から継承されたメソッドの呼び出しを試みるステートメントの部分を探します。  
  
3. ステートメントを書き直して、メソッド呼び出しが行われないようにします。  
  
## <a name="see-also"></a>関連項目

- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
