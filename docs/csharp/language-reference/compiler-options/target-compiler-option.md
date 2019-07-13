---
title: -target (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: f29b656a3db08d35692e375fe2175ff75e510941
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499853"
---
# <a name="-target-c-compiler-options"></a>-target (C# コンパイラ オプション)
**-target** コンパイラ オプションは、次の 6 つの形式のいずれかで指定できます。  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] アプリの .exe ファイルを作成する場合。  
  
 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 .exe ファイルを作成する場合。  
  
 [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 コード ライブラリを作成する場合。  
  
 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 モジュールを作成する場合。  
  
 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Windows プログラムを作成する場合。  
  
 [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 .winmdobj 中間ファイルを作成する場合。  
  
 **-target:module** を指定しない限り、**-target** を使用すると、.NET Framework のアセンブリ マニフェストが出力ファイルに配置されます。 詳細については、「[共通言語ランタイムのアセンブリ](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)」と「[共通の属性](../../programming-guide/concepts/attributes/common-attributes.md)」を参照してください。  
  
 アセンブリ マニフェストは、コンパイル中の最初の .exe 出力ファイルに配置されます。 .exe 出力ファイルがない場合には、最初の DLL ファイルに配置されます。 たとえば、次のコマンド ラインでは、マニフェストは `1.exe` に配置されます。  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 コンパイラの 1 回のコンパイルで作成されるアセンブリ マニフェストは 1 つだけです。 コンパイルにおけるすべてのファイルの情報は、アセンブリ マニフェストに含まれます。 **-target:module** で作成されたもの以外のすべての出力ファイルには、アセンブリ マニフェストを含めることができます。 コマンド ラインで複数の出力ファイルを生成する場合は、アセンブリ マニフェストを 1 つだけ作成できます。このアセンブリ マニフェストは、コマンド ラインで指定した最初の出力ファイルに含める必要があります。 最初の出力ファイル (**-target:exe**、**-target:winexe**、**-target:library**、**-target:module**) にかかわらず、同じコンパイルで生成された他の出力ファイルはすべてモジュール (**-target:module**) でなければなりません。  
  
 アセンブリを作成する場合は、<xref:System.CLSCompliantAttribute> 属性を使用して、コードのすべてまたは一部が CLS 準拠であることを指定できます。  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 このコンパイラ オプションのプログラムによる設定の詳細については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
