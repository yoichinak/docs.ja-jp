---
title: <trace> の <listeners> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153374"
---
# <a name="listeners-element-for-trace"></a>\<トレース>の\<リスナー>要素
メッセージを収集、格納、およびルーティングするリスナーを指定します。 リスナーは、トレース出力を適切なターゲットに送ります。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<トレース>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<リスナー>**

## <a name="syntax"></a>構文  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>を追加する](add-element-for-listeners-for-trace.md)|`Listeners` コレクションにリスナーを追加します。|  
|[\<クリア>](clear-element-for-listeners-for-trace.md)|トレースの `Listeners` コレクションを削除します。|  
|[\<>を削除する](remove-element-for-listeners-for-trace.md)|`Listeners`コレクションからリスナーを削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## <a name="remarks"></a>解説  
 と<xref:System.Diagnostics.Debug><xref:System.Diagnostics.Trace>クラスは同じ**Listeners**コレクションを共有します。 これらのクラスの 1 つでリスナー オブジェクトをコレクションに追加すると、もう一方のクラスは同じリスナーを使用します。 .NET Framework に付属のリスナー クラスは、<xref:System.Diagnostics.TraceListener>クラスから派生します。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、**\<リスナー>** 要素を使用してリスナーと`MyListener``MyEventListener` **Listeners**コレクションを追加する方法を示しています。 `MyListener`と呼ばれる`MyListener.log`ファイルを作成し、そのファイルに出力を書き込みます。 `MyEventListener`は、イベント ログにエントリを作成します。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceListener>
- [トレースおよびデバッグ設定のスキーマ](index.md)
