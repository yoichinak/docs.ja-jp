---
title: 標準クエリ演算子のクエリ式構文 (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: 232793e63673ef51b650d8188fea5733d02fd1b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501773"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>標準クエリ演算子のクエリ式構文 (C#)
頻繁に使用される標準クエリ演算子の中には、C# 言語専用のキーワード構文が使用されているものがあります。こうした構文では、標準クエリ演算子を、"*クエリ式*" の一部として呼び出すことができます。 クエリ式は*メソッド ベース*の方法とは異なり、より読み取りやすいクエリの表現形式です。 クエリ式の句は、コンパイル時にクエリ メソッドへの呼び出しに変換されます。  
  
## <a name="query-expression-syntax-table"></a>クエリ式の構文表  
 次の表は、同等なクエリ式の句がある標準クエリ演算子の一覧です。  
  
|メソッド|C# のクエリ式の構文|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|明示的に型指定された範囲変数を使用します。例:<br /><br /> `from int i in numbers`<br /><br /> (詳しくは、「[from 句](../../../../csharp/language-reference/keywords/from-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> - または -<br /><br /> `group … by … into …`<br /><br /> (詳しくは、「[group 句](../../../../csharp/language-reference/keywords/group-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (詳しくは、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (詳しくは、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (詳しくは、「[select 句](../../../../csharp/language-reference/keywords/select-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|複数の `from` 句を使用します。<br /><br /> (詳しくは、「[from 句](../../../../csharp/language-reference/keywords/from-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (詳しくは、「[where 句](../../../../csharp/language-reference/keywords/where-clause.md)」をご覧ください。)|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [実行方法による標準クエリ演算子の分類 (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
