---
title: フレンド アセンブリ (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 5de27643be8f5ddbf533ebb75b66666fc6bc148b
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748194"
---
# <a name="friend-assemblies-c"></a>フレンド アセンブリ (C#)
"*フレンド アセンブリ*" とは、別のアセンブリに [internal](../../../../csharp/language-reference/keywords/internal.md) として宣言されている型やメンバーにアクセスできるアセンブリです。 フレンド アセンブリとして指定した場合、public として宣言されていないその型とメンバーに、他のアセンブリからアクセスできるようになります。 この方法は、特に次の状況で利便性を発揮します。  
  
-   単体テスト中、テスト コードが別のアセンブリで実行されている状況で、そのテスト対象のアセンブリ内の `internal` メンバーにアクセスしなければならないとき。  
  
-   クラス ライブラリの開発中、そのライブラリへの追加機能が別のアセンブリにある状況で、既存アセンブリ内の `internal` メンバーにアクセスしなければならないとき。  
  
## <a name="remarks"></a>解説  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を利用し、特定のアセンブリの 1 つまたは複数のフレンド アセンブリを特定できます。 次の例では、アセンブリ A で <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を利用し、アセンブリ `AssemblyB` をフレンド アセンブリとして指定しています。 これでアセンブリ `AssemblyB` は、アセンブリ A の中で `internal` として宣言されているすべての型とメンバーにアクセスすることができます。  
  
> [!NOTE]
>  別のアセンブリ (アセンブリ *A*) の内部型または内部メンバーにアクセスするアセンブリ (アセンブリ `AssemblyB`) をコンパイルする際は、**/out** コンパイラ オプションを使用して、出力ファイル (.exe または .dll) の名前を明示的に指定する必要があります。 この指定は必ず行ってください。コンパイラが外部参照にバインドする時点ではまだ、ビルド中のアセンブリの名前が生成されていないためです。 詳細については、「[/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md)」を参照してください。  
  
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
  
 `internal` な型とメンバーにアクセスできるのは、明示的にフレンドとして指定されたアセンブリだけです。 たとえば、アセンブリ B がアセンブリ A のフレンドで、アセンブリ C がアセンブリ B を参照している場合、A の `internal` 型に C からアクセスすることはできません。  
  
 コンパイラは、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡されるフレンド アセンブリ名の基本検証を実行します。 アセンブリ *A* が *B* をフレンド アセンブリとして宣言する場合、検証規則は次のとおりです。  
  
-   アセンブリ *A* に厳密な名前が付けられている場合、アセンブリ *B* にも厳密な名前が付けられている必要があります。 属性に渡されるフレンド アセンブリ名は、アセンブリ名と、アセンブリ *B* の署名に使用される厳密名キーの公開キーで構成されている必要があります。  
  
     <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡すフレンド アセンブリ名として、アセンブリ *B* の厳密な名前を指定することはできません。アセンブリのバージョン、カルチャ、アーキテクチャ、公開キー トークンは含めないでください。  
  
-   アセンブリ *A* が厳密名でない場合、フレンド アセンブリの名前は、アセンブリ名のみで構成されている必要があります。 詳細については、「[方法 :署名のないフレンド アセンブリを作成する (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
  
-   アセンブリ *B* に厳密な名前が付けられている場合、プロジェクトの設定またはコマンド ラインの `/keyfile` コンパイラ オプションを使用してアセンブリ *B* の厳密名キーを指定する必要があります。 詳細については、「[方法 :署名されたフレンド アセンブリを作成する (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)」を参照してください。  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> クラスも型を共有する機能を提供しますが、次のような違いがあります。  
  
-   フレンド アセンブリはアセンブリ全体に適用されますが、<xref:System.Security.Permissions.StrongNameIdentityPermission> は個々の型に適用されます。  
  
-   アセンブリ *B* との間で共有したい型がアセンブリ *A* に数百個存在する場合、そのすべてに対して <xref:System.Security.Permissions.StrongNameIdentityPermission> を追加する必要があります。 フレンド アセンブリを使用した場合、フレンド関係を 1 回宣言するだけで済みます。  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> を使用する場合、共有する型をパブリックとして宣言する必要があります。 フレンド アセンブリを使用する場合、共有する型は `internal` として宣言されます。  
  
 アセンブリの `internal` な型とメソッドにモジュール ファイル (.netmodule 拡張子の付いたファイル) からアクセスする方法については、「[/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [方法: 署名のないフレンド アセンブリを作成する (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [方法: 署名されたフレンド アセンブリを作成する (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
- [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)
