---
title: <source> 要素
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153296"
---
# <a name="source-element"></a>\<ソース>要素
トレース メッセージを開始するトレース ソースを指定します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<ソース>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ソース>**

## <a name="syntax"></a>構文  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|省略可能な属性です。<br /><br /> トレース ソースの名前を指定します。|  
|`switchName`|省略可能な属性です。<br /><br /> アプリケーション内のトレース スイッチ インスタンスの名前を指定します。 `<switches>`スイッチが要素内で識別されない場合、値はスイッチのレベルを指定します。|  
|`switchType`|省略可能な属性です。<br /><br /> トレース スイッチの種類を指定します。 存在する場合、型は有効なクラス名である必要があり、空の文字列にすることはできません。|  
|`extraAttribute`|省略可能な属性です。<br /><br /> そのトレース ソースのメソッドによって識別されるトレース ソース固有<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>の属性の値を指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<リスナー>](listeners-element-for-source.md)|メッセージを収集、格納、およびルーティングするリスナーが含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
  
## <a name="remarks"></a>解説  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、要素を`<source>`使用してトレース ソース`mySource`を追加し、という名前`sourceSwitch`のソース スイッチのレベルを設定する方法を示しています。 トレース情報をコンソールに書き込むコンソール トレース リスナーが追加されます。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース スイッチ](../../../debug-trace-profile/trace-switches.md)
