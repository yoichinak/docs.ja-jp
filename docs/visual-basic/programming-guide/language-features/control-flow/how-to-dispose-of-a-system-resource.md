---
title: '方法: システム リソースを破棄する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: c780ee1a174ad044593960bc30a3ee2e1f929390
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583143"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>方法: システム リソースを破棄する (Visual Basic)
@No__t_0 ブロックを使用すると、コードがブロックを終了したときに、システムがリソースを破棄することを保証できます。 これは、大量のメモリを消費するシステムリソースを使用している場合や、他のコンポーネントでも使用する必要がある場合に便利です。  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>コードが終了したときにデータベース接続を破棄するには  
  
1. ソースファイルの先頭に、データベース接続に適した[Imports ステートメント (.Net 名前空間と型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)が含まれていることを確認してください (この場合は <xref:System.Data.SqlClient>)。  
  
2. @No__t_1 ステートメントと `End Using` ステートメントを使用して、`Using` ブロックを作成します。 ブロック内で、データベース接続を扱うコードを配置します。  
  
3. 接続を宣言し、そのインスタンスを `Using` ステートメントの一部として作成します。  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     ハンドルされない例外の場合を含め、ブロックを終了する方法に関係なく、システムはリソースを破棄します。  
  
     スコープがブロックに限定されているため、`Using` ブロックの外部から `sqc` にアクセスできないことに注意してください。  
  
     この同じ手法を、ファイルハンドルや COM ラッパーなどのシステムリソースでも使用できます。 @No__t_1 ブロックを終了した後で、リソースを他のコンポーネントで使用できるようにする場合は、`Using` ブロックを使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.SqlClient.SqlConnection>
- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)
