---
title: '方法: リフレクションを使用してアセンブリのメタデータをクエリする (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 52b961c5a016754964285221e252965ff89efd26
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485230"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>方法: リフレクションを使用してアセンブリのメタデータをクエリする (LINQ) (C#)

.NET Framework クラス ライブラリのリフレクション API を使用すると、.NET アセンブリ内のメタデータを調べ、そのアセンブリ内にある型、型メンバー、パラメーターなどのコレクションを作成できます。 これらのコレクションは、ジェネリック `IEnumerable` インターフェイスをサポートするため、LINQ を使用して照会できます。  
  
次の例では、LINQ でリフレクションを使用して、指定した検索条件に一致するメソッドについてのメタデータを取得する方法を示します。 この例のクエリでは、配列などの列挙可能な型を返すすべてのメソッドの名前をアセンブリ内で検索します。  
  
## <a name="example"></a>例  
  
```csharp  
using System.Reflection;  
using System.IO;  
namespace LINQReflection  
{  
    class ReflectionHowTO  
    {  
        static void Main(string[] args)  
        {  
            Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
            var pubTypesQuery = from type in assembly.GetTypes()  
                        where type.IsPublic  
                            from method in type.GetMethods()  
                            where method.ReturnType.IsArray == true   
                                || ( method.ReturnType.GetInterface(  
                                    typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                                && method.ReturnType.FullName != "System.String" )  
                            group method.ToString() by type.ToString();  
  
            foreach (var groupOfMethods in pubTypesQuery)  
            {  
                Console.WriteLine("Type: {0}", groupOfMethods.Key);  
                foreach (var method in groupOfMethods)  
                {  
                    Console.WriteLine("  {0}", method);  
                }  
            }  
  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
    }    
}  
```  
  
 この例では、<xref:System.Reflection.Assembly.GetTypes%2A> メソッドを使用して、指定したアセンブリ内の型の配列を返します。 パブリック型のみが返されるように、[where](../../../../csharp/language-reference/keywords/where-clause.md) フィルターが適用されています。 パブリック型ごとに、<xref:System.Type.GetMethods%2A> 呼び出しから返される <xref:System.Reflection.MethodInfo> 配列を使用してサブクエリが生成されます。 これらの結果はフィルター処理され、戻り値の型が配列か、<xref:System.Collections.Generic.IEnumerable%601> を実装する型であるメソッドのみが返されます。 最後に、型名をキーとして使用して、これらの結果がグループ化されます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 System.Linq 名前空間と System.IO 名前空間に `using` ディレクティブを使用して、C# コンソール アプリケーション プロジェクトを作成します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
