---
title: -define (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 46ceca3a84e8ffbe6d07886c1b93d062f3ccd2d1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305261"
---
# <a name="-define-c-compiler-options"></a>-define (C# コンパイラ オプション)
**-define** オプションは、`name` をプログラムのすべてのソース コード ファイル内のシンボルとして定義します。  
  
## <a name="syntax"></a>構文  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>引数  
 `name`, `name2`  
 定義する 1 つまたは複数のシンボルの名前。  
  
## <a name="remarks"></a>解説  
 **-define** オプションには、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) プリプロセッサ ディレクティブを使うのと同じ効果があります。ただし、コンパイラ オプションはプロジェクト内のすべてのファイルに対して有効である点が異なります。 ソース ファイルの [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) ディレクティブがこの定義を削除するまで、シンボルはソース ファイルで定義されたままになります。 -define オプションを使うと、あるファイルで指定されている `#undef` ディレクティブは、プロジェクト内の他のソース コード ファイルには影響しません。  
  
 このオプションで作成されるシンボルを [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)、[#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、および [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) で使う、ソース ファイルを条件付きでコンパイルできます。  
  
 **-d** は **-define** の省略形です。  
  
 **-define** では、シンボル名をセミコロンまたはコンマで区切ることにより、複数のシンボルを定義できます。 次に例を示します。  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 C# コンパイラ自体では、ソース コードで使うことができるシンボルやマクロは定義されません。すべてのシンボル定義はユーザーが定義する必要があります。  
  
> [!NOTE]
>  C++ などの言語とは異なり、C# の `#define` では、シンボルに値を割り当てることはできません。 たとえば、マクロの作成や定数の定義に `#define` を使うことはできません。 定数を定義する必要がある場合は、`enum` 変数を使います。 C++ スタイルのマクロを作成する場合は、ジェネリックなどで代用してください。 マクロはエラーを招きやすいため、C# では、マクロの使用は禁止され、代わりに、より安全な方法が提供されています。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[ビルド]** タブで、**[条件付きコンパイル シンボル]** ボックスに、定義するシンボルを入力します。 たとえば、次のコード例を使っている場合は、テキスト ボックスに「`xx`」と入力します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>」をご覧ください。  
  
## <a name="example"></a>例  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
