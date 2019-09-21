---
title: <remove> の <listeners> の <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920482"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<トレース > の\<リスナー \<> の > 要素を削除します
リスナーコレクションからリスナーを削除します。  
  
 \<configuration>  
\<system.diagnostics>  
\<トレース >  
\<リスナー >  
\<remove>  
  
## <a name="syntax"></a>構文  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**name**|必須の属性です。<br /><br /> **リスナー**コレクションから削除するリスナーの名前。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。 リスナーは、適切なターゲットにトレース出力を送信します。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`trace`|ASP.NET トレースサービスを構成します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>コレクションからを削除すると、、、 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>、および<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>の各メソッドの動作が変更されます。 `Listeners` 通常、メソッド`Fail`またはメソッドを呼び出すと、メッセージボックスが表示されますが`Listeners` 、 <xref:System.Diagnostics.DefaultTraceListener>がコレクションに含まれていない場合は、メッセージボックスは表示されません。 `Assert`  
  
## <a name="example"></a>例  
 次の例は、トレース**リスナー**コレクションから既定のトレースリスナーを削除する方法を示しています。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [トレースおよびデバッグ設定のスキーマ](index.md)
