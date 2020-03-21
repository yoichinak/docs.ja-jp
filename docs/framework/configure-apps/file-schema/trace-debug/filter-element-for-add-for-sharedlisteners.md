---
title: <filter>の<add>要素<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153454"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<共有リスナー>の\<追加>の\<フィルター>要素
`sharedListeners` コレクションのリスナーにフィルターを追加します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<共有リスナー>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>を追加する**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<フィルター>**

## <a name="syntax"></a>構文  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**型**|必須の属性です。<br /><br /> フィルタの種類を指定します。 型の完全名 (<xref:System.Type.FullName%2A?displayProperty=nameWithType>プロパティの形式) のみを使用するか、アセンブリ情報を含む完全修飾型名 (プロパティの形式) を<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>使用できます。 完全修飾型名の作成については、「完全修飾[型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。|  
|**初期化データ**|省略可能な属性です。<br /><br /> 指定したクラスのコンストラクターに渡される文字列。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sharedListeners`|任意のソースまたはトレース要素が参照できるリスナーのコレクション。|  
|`add`|リスナーを**sharedListeners**コレクションに追加します。|  
  
## <a name="remarks"></a>解説  
 `<add>`リスナーが`<sharedListeners>`要素の要素で定義されている場合、そのリスナーのフィルターは、要素の子要素で`<filter>`定義する`<add>`必要があります。  
  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 要素を使用してコレクション内の`<filter>`トレース リスナー`console`にフィルターを追加する方法を次の`sharedListeners`例に示します。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [トレースおよびデバッグ設定のスキーマ](index.md)
