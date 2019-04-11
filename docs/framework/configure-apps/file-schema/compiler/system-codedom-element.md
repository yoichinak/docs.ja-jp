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
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101615"
---
# <a name="systemcodedom-element"></a>\<system.codedom > 要素
使用可能な言語プロバイダーのコンパイラ構成設定を指定します。  
  
 \<configuration > 要素  
\<system.codedom > 要素  
  
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
|[\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|0 個以上の [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 要素を含むコンパイラ構成要素のコンテナー。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="net-framework-version-20"></a>.NET framework Version 2.0  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)要素にはなど、.NET Framework と共にインストールされる既定のプロバイダーだけでなく、コンピューターにインストールされている言語プロバイダーのコンパイラ構成設定が含まれています、<xref:Microsoft.CSharp.CSharpCodeProvider> 、<xref:Microsoft.VisualBasic.VBCodeProvider>します。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素は、0 個以上含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素。 各[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。  
  
 開発者やコンパイラ ベンダーの構成設定に追加できますマシン構成ファイル (Machine.config) 新しい<xref:System.CodeDom.Compiler.CodeDomProvider>実装します。 使用して、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>プログラムで、既定の言語プロバイダーとコンパイラ構成設定、コンピューター上で識別される言語プロバイダーを列挙するメソッド。  
  
> [!NOTE]
>  .NET Framework バージョン 1.0 および 1.1 では、.NET Framework によって提供されるプロバイダーがで識別される既定の言語で、 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素。 識別されない既定の言語プロバイダー、.NET Framework version 2.0 で、 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素を使用して列挙できますが、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>メソッド。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET framework Version 1.0 および 1.1  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)要素には、コンピューター上の言語プロバイダーのコンパイラ構成設定が含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素は、0 個以上含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素。 各[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。  
  
 .NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。 開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、マシン構成ファイルおよびアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、通常のコンパイラ構成を示しています。  
  
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
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [コンパイラおよび言語プロバイダー設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [\<compiler> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
