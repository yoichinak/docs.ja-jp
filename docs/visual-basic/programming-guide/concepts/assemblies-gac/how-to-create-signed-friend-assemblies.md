---
title: '方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。'
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
ms.openlocfilehash: 4ff32015647a565f7f68e944ae028deb7f738e28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022273"
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。
この例では、厳密な名前を持つアセンブリと共にフレンド アセンブリを使用する方法を示します。 両方のアセンブリに厳密な名前が付けられている必要があります。 この例のアセンブリは両方とも同じキーを使用していますが、2 つのアセンブリそれぞれが別々のキーを使用することもできます。  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>署名付きアセンブリとフレンド アセンブリを作成するには  
  
1. コマンド プロンプトを開きます。  
  
2. 厳密な名前ツールで次のコマンド シーケンスを使用して、キー ファイルを生成し、公開鍵を表示します。 詳細については、次を参照してください。 [Sn.exe (厳密名ツール)](../../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
    1. この例で使用する厳密な名前キーを生成し、FriendAssemblies.snk ファイルに格納します。  
  
         `sn -k FriendAssemblies.snk`  
  
    2. FriendAssemblies.snk から公開鍵を抽出し、FriendAssemblies.publickey に追加します。  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. FriendAssemblies.publickey ファイルに格納されている公開鍵を表示します。  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. という名前の Visual Basic ファイルを作成する`friend_signed_A`次のコードを格納しています。 コードでは <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を使用して、フレンド アセンブリとして friend_signed_B を宣言します。  
  
     厳密な名前ツールは、実行するごとに新しい公開鍵を生成します。 このため、次の例に示すコード内の公開鍵を、ここで生成した公開鍵に置き換える必要があります。  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4. 次のコマンドを使用して friend_signed_A をコンパイルして署名します。  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5. という名前の Visual Basic ファイルを作成する`friend_signed_B`次のコードが含まれています。 friend_signed_A が friend_signed_B をフレンド アセンブリとして指定しているため、friend_signed_B 内のコードは、friend_signed_A の `Friend` 型とメンバーにアクセスできます。 このファイルには、次のコードが含まれています。  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6. 次のコマンドを使用して friend_signed_B をコンパイルして署名します。  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     コンパイラによって生成されたアセンブリの名前は、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡されたフレンド アセンブリ名と一致している必要があります。 使用して、アセンブリを明示的に設定することができます、`-out`コンパイラ オプション。 詳細については、次を参照してください。 [-(Visual Basic) を](../../../../visual-basic/reference/command-line-compiler/out.md)します。  
  
7. friend_signed_B.exe ファイルを実行します。  
  
     プログラムには、文字列"Class1.Test"が表示されます。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性と <xref:System.Security.Permissions.StrongNameIdentityPermission> クラスには類似点があります。 主な違いは、<xref:System.Security.Permissions.StrongNameIdentityPermission> はセキュリティ アクセス許可を要求することで特定のコード セクションを実行できますが、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性では `Friend` 型とメンバーの参照可能範囲を制御することです。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
- [フレンド アセンブリ](../../../../standard/assembly/friend-assemblies.md)
- [方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [-keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe (厳密名ツール)](../../../../framework/tools/sn-exe-strong-name-tool.md))
- [厳密な名前付きアセンブリの作成と使用](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)
