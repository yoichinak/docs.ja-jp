---
title: リストと配列の繰り返しフィールド-WCF 開発者向けの gRPC
description: コレクションが Protobuf によってどのように処理され、.NET コレクションにどのように関連しているかを理解します。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 740af8af39af9bf31be17ad831f481176e30d81f
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "73841397"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>リストと配列の繰り返しフィールド

リストは、`repeated` prefix キーワードを使用して Protobuf で指定されます。 次の例は、リストを作成する方法を示しています。

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

生成されたコードでは、`repeated` フィールドは、組み込みの .NET コレクション型ではなく、`Google.Protobuf.Collections.RepeatedField<T>` ジェネリック型によって表されます。 `RepeatedField<T>` 型には、リストをバイナリワイヤ形式にシリアル化および逆シリアル化するために必要なコードが含まれています。 <xref:System.Collections.Generic.IList%601> や <xref:System.Collections.Generic.IEnumerable%601>などの標準的な .NET コレクションインターフェイスがすべて実装されているため、LINQ クエリを使用したり、配列やリストに簡単に変換したりできます。

>[!div class="step-by-step"]
>[前へ](protobuf-nested-types.md)
>[次へ](protobuf-reserved.md)
