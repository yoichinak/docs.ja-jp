---
title: 軽減策:DataContractJsonSerializer での制御文字のシリアル化
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b26c8cc01b7af1c3b345d2f274a1d25a19d689
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789844"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>軽減策:DataContractJsonSerializer での制御文字のシリアル化

.NET Framework 4.7 以降では、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> での制御文字のシリアル化の方法が、ECMAScript V6 および V8 に準拠するように変更されました。 
 
## <a name="impact"></a>影響

.NET framework 4.6.2 以前のバージョンでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> で、ECMAScript V6 および V8 標準と互換性がある方法で `\b`、`\f`、`\t` などの一部の特殊制御文字がシリアル化されませんでした。

.NET Framework 4.7 以降のバージョンの .NET Framework を対象とするアプリの場合、これらの制御文字のシリアル化は ECMAScript V6 および V8 と互換性があります。 影響を受ける API は次のとおりです。

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>軽減策

.NET Framework 4.7 以降のバージョンの .NET Framework を対象とするアプリの場合、この動作は既定で有効になります。

この動作が望ましくない場合は、app.config または web.config ファイルの `<runtime>` セクションに次の行を追加して、この機能を無効にすることができます。

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>関連項目

- [.NET Framework 4.7 における再ターゲットの変更点](retargeting-changes-in-the-net-framework-4-7.md)
