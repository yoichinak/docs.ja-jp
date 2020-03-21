---
title: <system.codedom> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155389"
---
# <a name="systemcodedom-element"></a>\<要素>コードダム
使用可能な言語プロバイダーのコンパイラ構成設定を指定します。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;**\<コードダム>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<コンパイラ>](compilers-element.md)|コンパイラ構成要素のコンテナ。コンパイラ[\<>](compiler-element.md)要素が 0 個以上含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<構成>](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="remarks"></a>解説  
  
## <a name="net-framework-version-20"></a>.NET フレームワーク バージョン 2.0  
 [ \<system.codedom>](system-codedom-element.md)要素には、.NET Framework と共にインストールされる既定のプロバイダに加えて、<xref:Microsoft.CSharp.CSharpCodeProvider>コンピュータにインストールされている言語プロバイダのコンパイラ構成設定が<xref:Microsoft.VisualBasic.VBCodeProvider>含まれています。 [\<コンパイラ>](compilers-element.md)要素には、0 個以上[\<のコンパイラ>](compiler-element.md)要素が含まれています。 各[\<コンパイラ>要素は](compiler-element.md)、特定の言語プロバイダのコンパイラ構成属性を指定します。  
  
 開発者およびコンパイラ ベンダは、新しい<xref:System.CodeDom.Compiler.CodeDomProvider>実装用にマシン構成ファイル (Machine.config) に構成設定を追加できます。 このメソッド<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>を使用して、既定の言語プロバイダーと、コンピューターのコンパイラ構成設定で識別される言語プロバイダーの両方をプログラムで列挙します。  
  
> [!NOTE]
> .NET Framework バージョン 1.0 および 1.1 では、.NET Framework によって提供される既定の言語プロバイダーが[\<コンパイラ>](compilers-element.md)要素で識別されます。 .NET Framework Version 2.0 では、既定の言語プロバイダは[\<コンパイラ>](compilers-element.md)要素で識別されませんが、メソッドを<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>使用して列挙できます。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET フレームワーク バージョン 1.0 および 1.1  
 system.codedom>要素には、コンピューター上の言語プロバイダーのコンパイラ構成設定が含まれています。 [ \<](system-codedom-element.md) [\<コンパイラ>](compilers-element.md)要素には、0 個以上[\<のコンパイラ>](compiler-element.md)要素が含まれています。 各[\<コンパイラ>要素は](compiler-element.md)、特定の言語プロバイダのコンパイラ構成属性を指定します。  
  
 .NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。 開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、マシン構成ファイルおよびアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、一般的なコンパイラ構成を示しています。  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [構成ファイル スキーマ](../index.md)
- [コンパイラおよび言語プロバイダー設定スキーマ](index.md)
- [\<コンパイラ>要素](compiler-element.md)
