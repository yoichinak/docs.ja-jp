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
ms.openlocfilehash: 19f37095bd01b76fda8b1e29423c413dbdb06a65
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168918"
---
# <a name="systemcodedom-element"></a>\<system.string > 要素
使用可能な言語プロバイダーのコンパイラ構成設定を指定します。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<システムの codedom >**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|0 個以上の [\<compiler>](compiler-element.md) 要素を含むコンパイラ構成要素のコンテナー。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="net-framework-version-20"></a>.NET Framework バージョン2.0  
 System.string > 要素には、コンピューターにインストールされている言語プロバイダーのコンパイラ構成設定<xref:Microsoft.CSharp.CSharpCodeProvider>と、.NET Framework と共にインストールされる既定のプロバイダー (やなど) が含まれ[ます。 \<](system-codedom-element.md)<xref:Microsoft.VisualBasic.VBCodeProvider>. [ \<コンパイラの >](compilers-element.md)要素には、0個以上[ \<のコンパイラ >](compiler-element.md)要素が含まれています。 [各\<コンパイラ >](compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。  
  
 開発者やコンパイラベンダーは、新しい<xref:System.CodeDom.Compiler.CodeDomProvider>実装のために構成設定をマシン構成ファイル (machine.config) に追加できます。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>メソッドを使用して、コンピューター上のコンパイラ構成設定によって識別される既定の言語プロバイダーと言語プロバイダーの両方をプログラムによって列挙します。  
  
> [!NOTE]
> .NET Framework バージョン1.0 および1.1 では、.NET Framework によって提供される既定の言語プロバイダーは、 [ \<コンパイラの >](compilers-element.md)要素で識別されます。 .NET Framework バージョン2.0 では、 [ \<コンパイラの >](compilers-element.md)要素で既定の言語プロバイダーは識別されませんが、 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>メソッドを使用して列挙できます。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework バージョン1.0 および1.1  
 System.string > 要素には、コンピューター上の言語プロバイダーのコンパイラ構成設定が含まれています。 [ \<](system-codedom-element.md) [ \<コンパイラの >](compilers-element.md)要素には、0個以上[ \<のコンパイラ >](compiler-element.md)要素が含まれています。 [各\<コンパイラ >](compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。  
  
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
- [コンパイラおよび言語プロバイダー設定のスキーマ](index.md)
- [\<compiler> 要素](compiler-element.md)
