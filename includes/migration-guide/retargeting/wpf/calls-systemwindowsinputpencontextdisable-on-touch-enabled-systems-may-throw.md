---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761067"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>タッチ対応システムで System.Windows.Input.PenContext.Disable を呼び出すと ArgumentException がスローされることがある

|   |   |
|---|---|
|説明|一部の状況では、タッチ対応システムで内部 <strong>System.Windows.Intput.PenContext.Disable</strong> メソッドを呼び出すと、再入に起因して未処理の <code>T:System.ArgumentException</code> がスローされることがあります。|
|提案される解決策|この問題は、.NET Framework 4.7 では対処済みです。 例外を防ぐには、.NET Framework 4.7 以降のバージョンの .NET Framework にアップグレードします。|
|スコープ|エッジ|
|Version|4.6.1|
|型|再ターゲット中|

