---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234464"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>タッチ対応システムで System.Windows.Input.PenContext.Disable を呼び出すと ArgumentException がスローされることがある

|   |   |
|---|---|
|説明|一部の状況では、タッチ対応システムで内部 <strong>System.Windows.Intput.PenContext.Disable</strong> メソッドを呼び出すと、再入に起因して未処理の <code>T:System.ArgumentException</code> がスローされることがあります。|
|提案される解決策|この問題は、.NET Framework 4.7 では対処済みです。 例外を防ぐには、.NET Framework 4.7 以降のバージョンの .NET Framework にアップグレードします。|
|スコープ|エッジ|
|Version|4.6.1|
|型|再ターゲット中|
