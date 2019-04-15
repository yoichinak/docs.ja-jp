---
title: '方法: 署名のないフレンド アセンブリを作成する (C#)'
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 6bc2d807b3d1cf6c82a9ba6303139b9758581f35
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318235"
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>方法: 署名のないフレンド アセンブリを作成する (C#)
この例では、署名のないアセンブリと共にフレンド アセンブリを使用する方法を示します。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>署名のないアセンブリとフレンド アセンブリを作成するには  
  
1. コマンド プロンプトを開きます。  
  
2. 次のコードを含む、`friend_unsigned_A.` という名前の C# ファイルを作成します。 コードでは <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を使用して、フレンド アセンブリとして friend_unsigned_B を宣言します。  
  
    ```csharp  
    // friend_unsigned_A.cs  
    // Compile with:   
    // csc /target:library friend_unsigned_A.cs  
    using System.Runtime.CompilerServices;  
    using System;  
  
    [assembly: InternalsVisibleTo("friend_unsigned_B")]  
  
    // Type is internal by default.  
    class Class1  
    {  
        public void Test()  
        {  
            Console.WriteLine("Class1.Test");  
        }  
    }  
  
    // Public type with internal member.  
    public class Class2  
    {  
        internal void Test()  
        {  
            Console.WriteLine("Class2.Test");  
        }  
    }  
    ```  
  
3. 次のコマンドを使用して friend_unsigned_A をコンパイルして署名します。  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4. 次のコードを含む、`friend_unsigned_B` という名前の C# ファイルを作成します。 friend_unsigned_A が friend_unsigned_B をフレンド アセンブリとして指定しているため、friend_unsigned_B 内のコードは、friend_unsigned_A の `internal` 型とメンバーにアクセスできます。  
  
    ```csharp  
    // friend_unsigned_B.cs  
    // Compile with:   
    // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            // Access an internal type.  
            Class1 inst1 = new Class1();  
            inst1.Test();  
  
            Class2 inst2 = new Class2();  
            // Access an internal member of a public type.  
            inst2.Test();  
  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
5. 次のコマンドを使用して friend_unsigned_B をコンパイルします。  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     コンパイラによって生成されるアセンブリの名前は、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡されるフレンド アセンブリ名と一致している必要があります。 `/out` コンパイラ オプションを使用して、出力アセンブリ (.exe または .dll) の名前を明示的に指定する必要があります。 詳しくは、「[/out (C# コンパイラ オプション)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md)」をご覧ください。  
  
6. friend_unsigned_B.exe ファイルを実行します。  
  
     このプログラムで 2 つの文字列が出力されます。"Class1.Test" と "Class2.Test" です。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性と <xref:System.Security.Permissions.StrongNameIdentityPermission> クラスには類似点があります。 主な違いは、<xref:System.Security.Permissions.StrongNameIdentityPermission> はセキュリティ アクセス許可を要求することで特定のコード セクションを実行できますが、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性では `internal` 型とメンバーの参照可能範囲を制御することです。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
- [フレンド アセンブリ](../../../../standard/assembly/friend-assemblies.md)
- [方法: 署名されたフレンド アセンブリを作成する (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)
