---
title: Protobuf messages-WCF 開発者向け gRPC
description: Protobuf メッセージを IDL で定義し、で生成する方法C#について説明します。
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543041"
---
# <a name="protobuf-messages"></a>Protobuf メッセージ

このセクションでは `.proto` ファイルでプロトコルバッファー (Protobuf) メッセージを宣言する方法について説明します。 ここでは、フィールドの数値と型の基本的な概念についてC#説明し、`protoc` コンパイラによって生成されるコードを見ていきます。 

この章の残りの部分では、Protobuf でさまざまな種類のデータがどのように表現されるかについて詳しく説明します。

## <a name="declaring-a-message"></a>メッセージの宣言

Windows Communication Foundation (WCF) では、次の例のように、株式市場取引アプリケーションの `Stock` クラスを定義できます。

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

Protobuf で同等のクラスを実装するには、それを `.proto` ファイルで宣言する必要があります。 その後、`protoc` コンパイラによって、ビルド処理の一部として .NET クラスが生成されます。

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

最初の行は、使用されている構文のバージョンを宣言します。 言語のバージョン3は2016でリリースされました。 これは、gRPC サービスに推奨されるバージョンです。

`option csharp_namespace` 行では、生成C#された型に使用する名前空間を指定します。 `.proto` ファイルが他の言語用にコンパイルされている場合、このオプションは無視されます。 Protobuf ファイルには、多くの場合、複数の言語の言語固有のオプションが含まれています。

`Stock` メッセージ定義では、4つのフィールドが指定されています。 各には、型、名前、およびフィールド番号があります。

## <a name="field-numbers"></a>フィールド番号

フィールド番号は Protobuf の重要な部分です。 これらは、バイナリエンコードデータ内のフィールドを識別するために使用されます。つまり、サービスのバージョンごとに変更することはできません。 長所は、下位互換性と上位互換性が可能であることです。 クライアントとサービスは、不足値が処理される可能性がある限り、認識していないフィールド番号を無視します。

バイナリ形式では、フィールド番号が型識別子と結合されます。 1 ~ 15 のフィールド番号は、その型で1バイトとしてエンコードできます。 16から2047の数値は2バイトになります。 何らかの理由でメッセージに2047を超えるフィールドが必要な場合は、より高い値にすることができます。 フィールド番号が 1 ~ 15 の1バイト識別子ではパフォーマンスが向上します。そのため、最も基本的で頻繁に使用されるフィールドで使用する必要があります。

## <a name="types"></a>型

型宣言は、Protobuf のネイティブスカラーデータ型を使用しています。詳細については、[次のセクション](protobuf-data-types.md)で説明します。 この章の残りの部分では、Protobuf の組み込み型について説明し、一般的な .NET 型にどのように関連しているかを示します。

> [!NOTE]
> Protobuf は `decimal` 型をネイティブでサポートしていないため、代わりに `double` が使用されます。 完全な10進数の有効桁数を必要とするアプリケーションについては、この章の次の部分にある10進数[に関するセクション](protobuf-data-types.md#decimals)を参照してください。

## <a name="the-generated-code"></a>生成されたコード

アプリケーションをビルドすると、Protobuf はメッセージごとにクラスを作成し、ネイティブな型をC#型にマップします。 生成される `Stock` 型には、次のシグネチャがあります。

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

生成される実際のコードは、これよりもはるかに複雑です。 その理由は、各クラスには、それ自体をバイナリワイヤ形式にシリアル化および逆シリアル化するために必要なすべてのコードが含まれているからです。

### <a name="property-names"></a>プロパティ名

Protobuf コンパイラは、プロパティ名に `PascalCase` を適用しましたが、`.proto` ファイルには `snake_case` でした。 [Protobuf スタイルガイド](https://developers.google.com/protocol-buffers/docs/style)では、メッセージ定義で `snake_case` を使用して、他のプラットフォームのコード生成によって想定される規則のケースが生成されるようにすることを推奨しています。

>[!div class="step-by-step"]
>[前へ](protocol-buffers.md)
>[次へ](protobuf-data-types.md)
