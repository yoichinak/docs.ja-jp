---
title: 競合 ETW イベント - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95f56a6c8b51c58ed36d5d0de428bf57b728009c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723941"
---
# <a name="contention-etw-events"></a>競合 ETW イベント

競合イベントは、ランタイムによって使用される <xref:System.Threading.Monitor?displayProperty=nameWithType> ロックまたはネイティブ ロックの競合が発生するたびに発生します。 競合は、あるスレッドが、別のスレッドが保持しているロックを待機しているときに発生します。

競合イベントが発生するキーワードとイベントのレベルを次の表に示します  詳細については、次を参照してください。 [CLR ETW キーワードおよびレベル](clr-etw-keywords-and-levels.md)します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|情報提供 (4)|

次の表には、イベント情報が表示されます。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|競合が開始されたとき。 このイベントには、スレッドがロックの取得を待機する前のスピン時間は含まれません。このイベントが発生するのは、スレッドがロックの取得を待機するときだけです。|
|`ContentionStop`|91|競合が終了したとき。|

次の表では、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|フラグ|win:UInt8|マネージドの場合は 0、ネイティブの場合は 1 です。|
|ClrInstanceID|win:UInt16|CLR のインスタンスの一意の ID。|

## <a name="see-also"></a>関連項目

- [CLR ETW イベント](clr-etw-events.md)
