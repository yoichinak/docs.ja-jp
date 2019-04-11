---
ms.openlocfilehash: 9ad283af76085c228bedceb6db723a1d18b10210
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761117"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>サフィックスの "Start" または "Stop" のみで ETW イベント名を使い分けることができない

|   |   |
|---|---|
|説明|.NET Framework 4.6 と 4.6.1 では、2 つの ETW (Windows イベント トレーシング) イベント名の違いがサフィックスの &quot;Start&quot; または &quot;Stop&quot; のみのとき (たとえば、あるイベントの名前が <code>LogUser</code> で、別のイベントの名前が <code>LogUserStart</code> のとき)、ランタイムによって <xref:System.ArgumentException> がスローされます。 この場合、ランタイムはイベント ソースを作成できないため、ログ記録は生成できません。|
|提案される解決策|この例外を回避するには、サフィックスの &quot;Start&quot; または &quot;Stop&quot; でしか違いのないイベント名が存在しないようにします。この要件は .NET Framework 4.6.2 以降で削除されています。サフィックスの &quot;Start&quot; と &quot;Stop&quot; のみが異なるイベント名がランタイムによって区別されます。|
|スコープ|エッジ|
|Version|4.6|
|型|再ターゲット中|

