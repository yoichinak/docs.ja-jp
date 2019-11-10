---
title: Protobuf 入れ子になった型-gRPC (WCF 開発者向け)
description: Protobuf と gRPC での入れ子になったメッセージの種類、およびでC#の生成方法について説明します。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ec9fc522619230c1201bfef1e8128f7356936212
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "73841403"
---
# <a name="protobuf-nested-types"></a>Protobuf 入れ子型

とC#同様に、Protobuf を使用すると、他のクラス内のクラスを宣言できます。これにより、メッセージ定義を他のメッセージ内に入れ子にすることができます。 次の例は、入れ子になったメッセージ型を作成する方法を示しています。

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

生成C#されたコードでは、`Inner` 型は `HelloRequest` クラス内の入れ子になった静的 `Types` クラスで宣言されます。

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[前へ](protobuf-data-types.md)
>[次へ](protobuf-repeated.md)
