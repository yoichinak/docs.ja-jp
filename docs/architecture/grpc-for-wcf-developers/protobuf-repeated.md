---
title: リストと配列の繰り返しフィールド-WCF 開発者向けの gRPC
description: Protobuf がコレクションを処理する方法と、それらが .NET コレクションにどのように関連しているかを理解します。
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542960"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>リストと配列の繰り返しフィールド

プロトコルバッファー (Protobuf) でリストを指定するには、`repeated` prefix キーワードを使用します。 次の例は、リストを作成する方法を示しています。

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

生成されたコードでは、`repeated` フィールドは、組み込みの .NET コレクション型ではなく、`Google.Protobuf.Collections.RepeatedField<T>` ジェネリック型によって表されます。 

`RepeatedField<T>` 型には、リストをバイナリワイヤ形式にシリアル化および逆シリアル化するために必要なコードが含まれています。 <xref:System.Collections.Generic.IList%601> や <xref:System.Collections.Generic.IEnumerable%601>など、すべての標準的な .NET コレクションインターフェイスを実装します。 LINQ クエリを使用したり、配列またはリストに簡単に変換したりできます。

>[!div class="step-by-step"]
>[前へ](protobuf-nested-types.md)
>[次へ](protobuf-reserved.md)
