---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804361"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>タッチ対応システムで System.Windows.Input.PenContext.Disable を呼び出すと ArgumentException がスローされることがある

|   |   |
|---|---|
|説明|一部の状況では、タッチ対応システムで内部 <strong>System.Windows.Intput.PenContext.Disable</strong> メソッドを呼び出すと、再入に起因して未処理の <code>T:System.ArgumentException</code> がスローされることがあります。|
|提案される解決策|この問題は、.NET Framework 4.7 では対処済みです。 例外を防ぐには、.NET Framework 4.7 以降のバージョンの .NET Framework にアップグレードします。|
|スコープ|エッジ|
|Version|4.6.1|
|型|再ターゲット中|

