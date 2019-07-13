---
title: <filter> の <add> の <listeners> の <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: 5961125e1b8d0d0f5711f8b942b68ba71d61888f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701308"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<フィルター > 要素の\<追加 > の\<リスナー > の\<トレース >
内のリスナーにフィルターを追加、`Listeners`トレースのコレクション。  
  
 \<configuration>  
\<system.diagnostics>  
\<トレース >  
\<listeners>  
\<add>  
\<フィルター >  
  
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
|`type`|必須の属性です。<br /><br /> 継承する必要がありますフィルターの種類を指定します、<xref:System.Diagnostics.TraceFilter>クラス。 型の対応する型の名前空間修飾名を使用する<xref:System.Type.FullName%2A>プロパティに対応するアセンブリの情報を含む完全修飾型名を使用できます、<xref:System.Type.AssemblyQualifiedName%2A>プロパティ。 完全修飾型名については、次を参照してください。[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)します。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定したフィルター クラスのコンス トラクターに渡された文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
|`listeners`|収集、格納、およびメッセージをルーティングするリスナーが含まれています。 リスナーでは、適切なターゲットのトレースを出力します。|  
|`add`|`Listeners` コレクションにリスナーを追加します。|  
  
## <a name="remarks"></a>Remarks  
 `<filter>`で要素を含める必要があります、`<add>`リスナーの種類を指定するトレース リスナーの要素で定義されているリスナーの名前だけでなく、 [\<上 sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)します。 リスナーが定義されている場合、 [\<上 sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)、リスナーのフィルターは、その要素で定義する必要があります。  
  
 この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、`<filter>`リスナーにフィルターを追加する要素`console`で、`Listeners`としてフィルター イベント レベルを指定して、トレース`Error`します。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
