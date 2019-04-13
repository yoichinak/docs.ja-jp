---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761077"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>try 領域で IL ret が許可されない

|   |   |
|---|---|
|説明|JIT64 Just-In-Time コンパイラとは異なり、(.NET Framework 4.6 で使用される) RyuJIT では、try 領域で IL ret 命令が許可されません。 ECMA-335 仕様により try 領域から戻ることは許可されておらず、そうした IL を生成する既知のマネージド コンパイラはありません。 ただし、JIT64 コンパイラは、リフレクション出力を使用して生成される場合にはこうした IL を実行します。|
|提案される解決策|try 領域に ret オペコードを含む IL をアプリが生成する場合、そのアプリでは .NET Framework 4.5 を対象にして以前の JIT を使用し、この中断を回避できます。 あるいは、try 領域の後に戻るように生成後の IL を更新できます。|
|スコープ|エッジ|
|Version|4.6|
|型|再ターゲット中|

