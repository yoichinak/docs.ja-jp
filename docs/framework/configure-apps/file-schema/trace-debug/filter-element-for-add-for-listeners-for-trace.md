---
title: <filter>用<listeners>の<add>要素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153467"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<トレース>のリスナー \<>の追加\<>のフィルター>要素\<
`Listeners`コレクション内のトレースのリスナーにフィルターを追加します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<トレース>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<リスナー>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>を追加する**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<フィルター>**

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
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーが含まれています。 リスナーは、トレース出力を適切なターゲットに送ります。|  
|`add`|`Listeners` コレクションにリスナーを追加します。|  
  
## <a name="remarks"></a>解説  
 要素`<filter>`は[\<、sharedListeners ](sharedlisteners-element.md) `<add>`>で定義されたリスナーの名前だけでなく、リスナーの型を指定するトレース リスナーの要素に含まれている必要があります。 リスナーが[\<sharedListeners>](sharedlisteners-element.md)で定義されている場合は、そのリスナーのフィルターがその要素で定義されている必要があります。  
  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の`<filter>`例では、要素を使用して、コレクション内のトレース用の`console`リスナーに`Listeners`フィルターを追加し、フィルター イベント レベルを`Error`として指定する方法を示します。  
  
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
- [トレースおよびデバッグ設定のスキーマ](index.md)
