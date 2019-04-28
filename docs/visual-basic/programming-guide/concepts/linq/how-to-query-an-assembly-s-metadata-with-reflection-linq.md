---
title: '方法: リフレクション (LINQ) (Visual Basic) を使用してアセンブリのメタデータを照会します。'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: b5b74e27d4cfeb4360d9c743d16c16dc82134038
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644672"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>方法: リフレクション (LINQ) (Visual Basic) を使用してアセンブリのメタデータを照会します。
次の例では、LINQ でリフレクションを使用して、指定した検索条件に一致するメソッドについてのメタデータを取得する方法を示します。 この例のクエリでは、配列などの列挙可能な型を返すすべてのメソッドの名前をアセンブリ内で検索します。  
  
## <a name="example"></a>例  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
Module Module1  
  
    Sub Main()  
        Dim asmbly As Assembly =   
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()   
                            Where type.IsPublic   
                            From method In type.GetMethods()   
                            Where method.ReturnType.IsArray = True   
                            Let name = method.ToString()   
                            Let typeName = type.ToString()   
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 この例では、<xref:System.Reflection.Assembly.GetTypes%2A> メソッドを使用して、指定したアセンブリ内の型の配列を返します。 [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)パブリック型のみが返されるようにフィルターが適用されます。 パブリック型ごとに、<xref:System.Type.GetMethods%2A> 呼び出しから返される <xref:System.Reflection.MethodInfo> 配列を使用してサブクエリが生成されます。 これらの結果はフィルター処理され、戻り値の型が配列か、<xref:System.Collections.Generic.IEnumerable%601> を実装する型であるメソッドのみが返されます。 最後に、型名をキーとして使用して、これらの結果がグループ化されます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll および System.Linq 名前空間の `Imports` ステートメントを参照設定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
