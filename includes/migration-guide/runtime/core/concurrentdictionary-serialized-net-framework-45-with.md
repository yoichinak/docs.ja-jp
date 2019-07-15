---
ms.openlocfilehash: b7953aab434de3b081f22acc43cf6c4a00ac0742
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858564"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>NetDataContractSerializer を使用して .NET Framework 4.5 でシリアル化された ConcurrentDictionary は、.NET Framework 4.5.1 または 4.5.2 で逆シリアル化できない

|   |   |
|---|---|
|説明|型に対する内部的な変更のため、<xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> を使って .NET Framework 4.5 でシリアル化された <xref:System.Collections.Concurrent.ConcurrentDictionary%602> オブジェクトは、.NET Framework 4.5.1 または .NET Framework 4.5.2 では逆シリアル化できません。反対の方向 (.NET Framework 4.5.x でシリアル化して、.NET Framework 4.5 で逆シリアル化する) は動作することに注意してください。 同様に、すべての 4.x バージョン間のシリアル化は、.NET Framework 4.6 で機能します。 .NET Framework の 1 つのバージョンでのシリアル化と逆シリアル化は影響を受けません。|
|提案される解決策|.NET Framework 4.5 と .NET Framework 4.5.1/4.5.2 の間で <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> のシリアル化と逆シリアル化を行う必要がある場合は、<xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> の代わりに、<xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> または <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> シリアライザーなど、代替のシリアライザーを使う必要があります。または、この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって解決できます。|
|スコープ|マイナー|
|Version|4.5.1|
|型|ランタイム|

