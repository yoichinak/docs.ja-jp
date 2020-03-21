---
title: <compilers> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155415"
---
# <a name="compilers-element"></a>\<コンパイラは要素>
コンパイラ構成要素のコンテナ。コンパイラ[\<>](compiler-element.md)要素が 0 個以上含まれています。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<コードダム>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<コンパイラ>**

## <a name="syntax"></a>構文  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<コンパイラ>要素](compiler-element.md)|言語プロバイダーのコンパイラ構成属性を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<要素>構成](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<要素>コードダム](system-codedom-element.md)|使用可能な言語プロバイダーのコンパイラ構成設定を指定します。|  
  
## <a name="remarks"></a>解説  
 コンパイラ>要素には、コンピューター上の言語プロバイダーのコンパイラ構成設定が含まれています。 [ \<](compilers-element.md) 各[\<コンパイラ>要素は](compiler-element.md)、特定の言語プロバイダのコンパイラ構成属性を指定します。  
  
 .NET Framework では、マシン構成ファイル (Machine.config) でコンパイラと言語の初期設定を定義します。 開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> の実装のために構成設定を追加することができます。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、マシン構成ファイルおよびアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、一般的なコンパイラ構成要素を示しています。  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler
          language="c#;cs;csharp"
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
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
