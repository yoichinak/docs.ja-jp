---
title: Protobuf 列挙型-WCF 開発者向け gRPC
description: Protobuf で列挙型を宣言して使用する方法について説明します。
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543145"
---
# <a name="protobuf-enumerations"></a>Protobuf 列挙型

Protobuf は列挙型をサポートしています。 前のセクションでこのサポートを確認しました。ここでは、列挙型を使用して `Oneof` フィールドの型を決定しました。 独自の列挙型を定義すると、Protobuf は列挙型にC#コンパイルします。 

さまざまな言語で Protobuf を使用できるため、列挙型の名前付け規則は規則C#とは異なります。 ただし、コードジェネレーターは、名前を従来C#のケースに変換します。 フィールド名に対応する Pascal 形式が列挙名で始まる場合は、その名前が削除されます。

たとえば、次の Protobuf 列挙では、フィールドの先頭に `ACCOUNT_STATUS`が付きます。 このプレフィックスは、Pascal 形式の列挙名、`AccountStatus`に相当します。

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

ジェネレーターは、次C#のコードと同等の列挙型を作成します。

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

Protobuf 列挙型の定義には、最初のフィールドとして0の定数を*指定しなければなりません*。 と同様C#に、同じ値を持つ複数のフィールドを宣言できます。 ただし、列挙型の `allow_alias` オプションを使用して、このオプションを明示的に有効にする必要があります。

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

列挙は、`.proto` ファイルの最上位レベルで宣言することも、メッセージ定義内で入れ子にすることもできます。 入れ子になったメッセージと同様に、入れ子になった列挙型は、生成された message クラスの `.Types` 静的クラス内で宣言されます。

Protobuf で生成された列挙型に[[Flags]](xref:System.FlagsAttribute)属性を適用する方法はありません。 Protobuf はビットごとの列挙の組み合わせを認識しません。 次の例を見てください。

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

`product.AvailableIn` を `Region.NorthAmerica | Region.SouthAmerica`に設定すると、`3`整数値としてシリアル化されます。 クライアントまたはサーバーが値を逆シリアル化しようとすると、`3`の列挙型の定義に一致するものが見つかりません。 結果は `Region.None`になります。

Protobuf で複数の列挙値を操作する最善の方法は、列挙型の `repeated` フィールドを使用することです。

>[!div class="step-by-step"]
>[前へ](protobuf-any-oneof.md)
>[次へ](protobuf-maps.md)
