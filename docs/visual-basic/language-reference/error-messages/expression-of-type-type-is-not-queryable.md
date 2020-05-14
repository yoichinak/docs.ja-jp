---
title: 型 <type> の式はクエリ不可能です
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 121c0a95a3a6bb695d9c73347c733cba215a0de4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801622"
---
# <a name="expression-of-type-type-is-not-queryable"></a>型 \<type> の式はクエリ不可能です
型 \<type> の式はクエリ不可能です。 LINQ プロバイダーに対してアセンブリ参照や名前空間インポートが不足していないことを確認してください。  
  
 クエリ可能型は、<xref:System.Linq>、<xref:System.Data.Linq>、および <xref:System.Xml.Linq> 名前空間で定義します。 LINQ クエリを実行するには、これらの名前空間の 1 つ以上をインポートする必要があります。  
  
 <xref:System.Linq> 名前空間により、LINQ を使用してコレクションや配列などのオブジェクトに対してクエリを実行できます。  
  
 <xref:System.Data.Linq> 名前空間により、LINQ を使用して ADO.NET データセットと SQL Server データベースに対してクエリを実行できます。  
  
 <xref:System.Xml.Linq> 名前空間により、LINQ を使用して XML に対してクエリを実行し、Visual Basic の XML 機能を使用できます。  
  
 **エラー ID:** BC36593  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. <xref:System.Linq>、<xref:System.Data.Linq>、または <xref:System.Xml.Linq> 名前空間の `Import` ステートメントをコード ファイルに追加します。 プロジェクト デザイナー (**マイ プロジェクト**) の **[参照]** ページを使用して、プロジェクトの名前空間をインポートすることもできます。  
  
2. クエリのソースとして指定した型がクエリ可能型であることを確認します。 つまり、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を実装する型です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
