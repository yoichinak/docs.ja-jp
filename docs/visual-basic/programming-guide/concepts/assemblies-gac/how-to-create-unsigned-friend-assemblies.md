---
title: '方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
ms.openlocfilehash: 4771d0fe116d1532c270cf41b209665d5403a9b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339178"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。
この例では、署名のないアセンブリと共にフレンド アセンブリを使用する方法を示します。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>署名のないアセンブリとフレンド アセンブリを作成するには  
  
1. コマンド プロンプトを開きます。  
  
2. という名前の Visual Basic ファイルを作成する`friend_signed_A.`次のコードを格納しています。 コードでは <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を使用して、フレンド アセンブリとして friend_signed_B を宣言します。  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3. 次のコマンドを使用して friend_signed_A をコンパイルして署名します。  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4. という名前の Visual Basic ファイルを作成する`friend_unsigned_B`次のコードを格納しています。 friend_unsigned_A が friend_unsigned_B をフレンド アセンブリとして指定しているため、friend_unsigned_B 内のコードは、friend_unsigned_A の `Friend` 型とメンバーにアクセスできます。  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5. 次のコマンドを使用して friend_signed_B をコンパイルします。  
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     コンパイラによって生成されるアセンブリの名前は、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡されるフレンド アセンブリ名と一致している必要があります。 使用して、アセンブリを明示的に設定することができます、`/out`コンパイラ オプション。  
  
6. friend_signed_B.exe ファイルを実行します。  
  
     プログラムでは、2 つの文字列が表示されます。"Class1.Test" と "Class2.Test" です。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性と <xref:System.Security.Permissions.StrongNameIdentityPermission> クラスには類似点があります。 主な違いは、<xref:System.Security.Permissions.StrongNameIdentityPermission> はセキュリティ アクセス許可を要求することで特定のコード セクションを実行できますが、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性では `Friend` 型とメンバーの参照可能範囲を制御することです。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
- [フレンド アセンブリ](../../../../standard/assembly/friend-assemblies.md)
- [方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [プログラミング ガイドの概念](../../../../visual-basic/programming-guide/concepts/index.md)
