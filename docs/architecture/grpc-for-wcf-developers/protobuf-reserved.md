---
title: Protobuf の予約済みフィールド-WCF 開発者向け gRPC
description: バージョン間の互換性のために予約されているフィールドについて説明します。
ms.date: 09/09/2019
ms.openlocfilehash: 50082a1aab2e7707a1839b9d56455124a9e4a6a1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542977"
---
# <a name="protobuf-reserved-fields"></a>Protobuf 予約フィールド

プロトコルバッファー (Protobuf) での下位互換性の保証は、常に同じデータ項目を表すフィールド番号に依存します。 新しいバージョンのサービスでメッセージからフィールドが削除された場合、そのフィールド番号は再利用しないでください。 これを行うには、`reserved` キーワードを使用します。 

`displayName` フィールドと `marketId` フィールドが、前に定義した `Stock` メッセージから削除された場合は、次の例のようにフィールド番号を予約する必要があります。

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

また、今後追加される可能性のあるフィールドのプレースホルダーとして `reserved` キーワードを使用することもできます。 `to` キーワードを使用して、連続するフィールド番号を範囲として表すことができます。

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[前へ](protobuf-repeated.md)
>[次へ](protobuf-any-oneof.md)
