---
title: フレンド アセンブリ (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68671197"
---
# <a name="friend-assemblies"></a>フレンド アセンブリ

"*フレンド アセンブリ*" とは、別のアセンブリに [internal](../../csharp/language-reference/keywords/internal.md) (C# の場合、または Visual Basic では [Friend](../../visual-basic/language-reference/modifiers/friend.md)) として宣言されている型やメンバーにアクセスできるアセンブリです。 フレンド アセンブリとして指定した場合、public として宣言されていないその型とメンバーに、他のアセンブリからアクセスできるようになります。 この方法は、特に次の状況で利便性を発揮します。

- 単体テスト中、テスト コードが別のアセンブリで実行されている状況で、C# では `internal`、または Visual Basic では `Friend` としてマークされる、そのテスト対象のアセンブリ内のメンバーにアクセスしなければならないとき。

- クラス ライブラリの開発中、そのライブラリへの追加機能が別のアセンブリにある状況で、C# では `internal`、または Visual Basic では `Friend` としてマークされる、既存アセンブリ内のメンバーにアクセスしなければならないとき。

## <a name="remarks"></a>解説

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を利用し、特定のアセンブリの 1 つまたは複数のフレンド アセンブリを特定できます。 次の例では、アセンブリ A で <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を利用し、アセンブリ `AssemblyB` をフレンド アセンブリとして指定しています。 これで、アセンブリ `AssemblyB` は、アセンブリ A の中で、C# では `internal`、または Visual Basic では `Friend` としてマークされるすべての型とメンバーにアクセスすることができます。

> [!NOTE]
> 別のアセンブリ (アセンブリ *A*) の内部型または内部メンバーにアクセスするアセンブリ (アセンブリ `AssemblyB`) をコンパイルする際は、 **/out** コンパイラ オプションを使用して、出力ファイル (.exe または .dll) の名前を明示的に指定する必要があります。 この指定は必ず行ってください。コンパイラが外部参照にバインドする時点ではまだ、ビルド中のアセンブリの名前が生成されていないためです。 詳細については、「[-out (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/out-compiler-option.md)」または「[-除外 (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)」を参照してください。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

```vb
Imports System.Runtime.CompilerServices
Imports System
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

---

`internal` 型とメンバー (C# の場合、または Visual Basic では `Friend`) にアクセスできるのは、明示的にフレンドとして指定されたアセンブリだけです。 たとえば、アセンブリ B がアセンブリ A のフレンドで、アセンブリ C がアセンブリ B を参照している場合、A の `internal` 型 (C# の場合、または Visual Basic では `Friend`) に C からアクセスすることはできません。

コンパイラは、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡されるフレンド アセンブリ名の基本検証を実行します。 アセンブリ *A* が *B* をフレンド アセンブリとして宣言する場合、検証規則は次のとおりです。

- アセンブリ *A* に厳密な名前が付けられている場合、アセンブリ *B* にも厳密な名前が付けられている必要があります。 属性に渡されるフレンド アセンブリ名は、アセンブリ名と、アセンブリ *B* の署名に使用される厳密名キーの公開キーで構成されている必要があります。

     <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡すフレンド アセンブリ名として、アセンブリ *B* の厳密な名前を指定することはできません。アセンブリのバージョン、カルチャ、アーキテクチャ、公開キー トークンは含めないでください。

- アセンブリ *A* が厳密名でない場合、フレンド アセンブリの名前は、アセンブリ名のみで構成されている必要があります。 詳細については、「[方法 :署名のないフレンド アセンブリを作成する (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)」または「[方法: 署名のないフレンド アセンブリを作成する (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)」を参照してください。

- アセンブリ *B* に厳密な名前が付けられている場合、プロジェクトの設定またはコマンド ラインの `/keyfile` コンパイラ オプションを使用してアセンブリ *B* の厳密名キーを指定する必要があります。 詳細については、「[方法 :署名されたフレンド アセンブリを作成する (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)」または「[方法: 署名されたフレンド アセンブリを作成する (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)」を参照してください。

 <xref:System.Security.Permissions.StrongNameIdentityPermission> クラスも型を共有する機能を提供しますが、次のような違いがあります。

- フレンド アセンブリはアセンブリ全体に適用されますが、<xref:System.Security.Permissions.StrongNameIdentityPermission> は個々の型に適用されます。

- アセンブリ *B* との間で共有したい型がアセンブリ *A* に数百個存在する場合、そのすべてに対して <xref:System.Security.Permissions.StrongNameIdentityPermission> を追加する必要があります。 フレンド アセンブリを使用した場合、フレンド関係を 1 回宣言するだけで済みます。

- <xref:System.Security.Permissions.StrongNameIdentityPermission> を使用する場合、共有する型をパブリックとして宣言する必要があります。 フレンド アセンブリを使用する場合、共有する型は `internal` (C# の場合、または Visual Basic では `Friend`) として宣言されます。

アセンブリの `internal` (C# の場合、または Visual Basic では `Friend`) な型とメソッドにモジュール ファイル (.netmodule 拡張子の付いたファイル) からアクセスする方法については、「[/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)」または「[/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [方法: 署名のないフレンド アセンブリを作成する (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [方法: 署名のないフレンド アセンブリを作成する (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [方法: 署名されたフレンド アセンブリを作成する (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [方法: 署名されたフレンド アセンブリを作成する (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [.NET のアセンブリ](index.md)
- [C# プログラミング ガイド](../../csharp/programming-guide/index.md)
- [プログラミングの概念](../../visual-basic/programming-guide/concepts/index.md)
