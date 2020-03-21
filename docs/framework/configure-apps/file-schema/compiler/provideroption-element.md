---
title: <providerOption> 要素
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155402"
---
# <a name="provideroption-element"></a>\<プロバイダーオプション>要素
言語プロバイダーのコンパイラ バージョン属性を指定します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<コードダム>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<コンパイラ>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<コンパイラ>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<プロバイダオプション>**

## <a name="syntax"></a>構文  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須の属性です。<br /><br /> オプションの名前を指定します。たとえば、"コンパイラバージョン" を使用します。|  
|`value`|必須の属性です。<br /><br /> オプションの値を指定します。たとえば、"v3.5" です。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<要素>構成](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<要素>コードダム](system-codedom-element.md)|使用可能な言語プロバイダーのコンパイラ構成設定を指定します。|  
|[\<コンパイラは要素>](compilers-element.md)|コンパイラ構成要素のコンテナ。0 個以上`<compiler>`の要素が含まれています。|  
|[\<コンパイラ>要素](compiler-element.md)|言語プロバイダーのコンパイラ構成属性を指定します。|  
  
## <a name="remarks"></a>解説  
 NET Framework Version 3.5 では、コード ドキュメント オブジェクト モデル (CodeDOM) コード プロバイダーは、`<providerOption>`要素を使用してプロバイダー固有のオプションをサポートできます。  
  
 .NET Framework 3.5 には、更新された .NET Framework 2.0 アセンブリが含まれており、新しい型を含む新しいバージョン 3.5 アセンブリが提供されます。 Microsoft C# および Visual Basic のコード プロバイダーは.NET Framework 2.0 アセンブリに含まれていますが、バージョン 3.5 コンパイラをサポートするように更新されました。 既定では、更新されたコード プロバイダーはバージョン 2.0 コンパイラのコードを生成します。 この要素を`<providerOption>`使用して、ターゲットコンパイラのバージョンを 3.5 に変更できます。 これを行うには、`name`属性に 「CompilerVersion」 を指定し、属性に "v3.5" を指定します。 `value` バージョン番号の前に小文字の "v" を付けなければなりません。  
  
 .NET Framework 2.0 Machine.config ファイルまたはルート Web.config ファイルに`<providerOption>`要素を追加することで、バージョン仕様をグローバルにすることができます。 Machine.config ファイルで既定のコンパイラ バージョンを 3.5 に更新する場合は、アプリケーション構成ファイルの`<providerOption>`要素を使用して、アプリケーションごとに 2.0 に戻すことができます。  
  
 CodeDOM コード プロバイダーの実装者は、型`providerOptions`<xref:System.Collections.Generic.IDictionary%602>のパラメーターを受け取るコンストラクターを提供することで、カスタム オプションを処理できます。  
  
## <a name="example"></a>例  
 C# コード プロバイダーのバージョン 3.5 を使用する必要があるを指定する方法を次の例に示します。  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [構成ファイル スキーマ](../index.md)
- [\<コンパイラは要素>](compilers-element.md)
- [完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [compilation の compilers の compiler 要素 (ASP.NET 設定スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
