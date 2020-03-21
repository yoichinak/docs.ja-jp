---
title: <filter>用<listeners>の<add>要素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153517"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<ソース>の\<リスナー>の\<追加>のフィルター>要素\<
トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<ソース>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ソース>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<リスナー>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>を追加する**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<フィルター>**

## <a name="syntax"></a>構文  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`type`|必須の属性です。<br /><br /> クラスから継承する必要があるフィルターの型を指定します<xref:System.Diagnostics.TraceFilter>。 型の名前空間修飾名を使用して、型の<xref:System.Type.FullName%2A>プロパティに対応するか、またはプロパティに対応するアセンブリ情報を含む完全修飾型名を<xref:System.Type.AssemblyQualifiedName%2A>使用できます。 完全修飾型名の詳細については、「完全修飾[型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したフィルター クラスのコンストラクターに渡される文字列。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーが含まれています。 リスナーは、トレース出力を適切なターゲットに送ります。|  
|`add`|トレース ソースの `Listeners` コレクションにリスナーを追加します。|  
  
## <a name="remarks"></a>解説  
 要素`<filter>`は[\<、sharedListeners ](sharedlisteners-element.md) `<add>`>で定義されたリスナーの名前だけでなく、リスナーの型を指定するトレース ソース リスナーの要素に含まれている必要があります。 リスナーが[\<sharedListeners>](sharedlisteners-element.md)で定義されている場合は、そのリスナーのフィルターがその要素で定義されている必要があります。  
  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、`<filter>`要素を使用して、コレクション内の`console``Listeners`トレース ソース`myTraceSource`のリスナーにフィルターを追加する方法を示しています。 `Error`  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [トレースおよびデバッグ設定のスキーマ](index.md)
