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
ms.openlocfilehash: 9c69ea7bf95b311a796ec29d90410a77b748c3c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705325"
---
# <a name="provideroption-element"></a>\<providerOption > 要素
言語プロバイダーのコンパイラ バージョン属性を指定します。  
  
 \<configuration >要素  
\<system.codedom>要素  
\<compilers >要素  
\<compiler> 要素  
\<providerOption > 要素  
  
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
|`name`|必須の属性です。<br /><br /> オプション; の名前を指定しますたとえば、"CompilerVersion"です。|  
|`value`|必須の属性です。<br /><br /> オプションの値を指定しますたとえば、"v3.5"とします。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<system.codedom > 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|使用可能な言語プロバイダーのコンパイラ構成設定を指定します。|  
|[\<compilers> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|コンパイラ構成要素のコンテナー0 個以上含む`<compiler>`要素。|  
|[\<compiler> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|言語プロバイダーのコンパイラ構成属性を指定します。|  
  
## <a name="remarks"></a>Remarks  
 .NET framework version 3.5 では、Code Document Object Model (CodeDOM) コード プロバイダーを使用してプロバイダーに固有のオプションをサポートできる、`<providerOption>`要素。  
  
 .NET Framework 3.5 では、更新された .NET Framework 2.0 アセンブリが含まれていて、新しい型を含む新しいバージョン 3.5 アセンブリを提供します。 Microsoft c# と Visual Basic コード プロバイダーは、.NET Framework 2.0 アセンブリに含まれるが、version 3.5 のコンパイラをサポートするが更新されました。 既定では、更新されたコード プロバイダーは、バージョン 2.0 コンパイラ用のコードを生成します。 使用することができます、 `<providerOption>` 3.5 をターゲット コンパイラのバージョンを変更する要素。 これを行うには、"CompilerVersion"を指定の`name`属性と"v3.5"用、`value`属性。 小文字の"v"のバージョン番号の前にする必要があります。  
  
 行うことができます、バージョン指定グローバルを追加して、`<providerOption>`を .NET Framework 2.0 Machine.config または Web.config ファイルのルート要素。 Machine.config ファイルで 3.5 に既定のコンパイラ バージョンを更新した場合ことができますに変更する戻るアプリケーションごとに 2.0 を使用して、`<providerOption>`アプリケーション構成ファイル内の要素。  
  
 CodeDOM コード プロバイダーの実装を受け取るコンス トラクターを提供することによってカスタム オプションを処理できる、`providerOptions`型のパラメーター<xref:System.Collections.Generic.IDictionary%602>します。  
  
## <a name="example"></a>例  
 次の例では、c# コード プロバイダーのバージョン 3.5 を使用する必要がありますを指定する方法を示します。  
  
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
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<compilers> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [(ASP.NET 設定スキーマ) compilation の compilers の compiler 要素](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
