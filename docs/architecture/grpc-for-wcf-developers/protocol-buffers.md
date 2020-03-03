---
title: プロトコルバッファー-WCF 開発者向け gRPC
description: GRPC ネットワークに使用されるプロトコルバッファーワイヤ形式の概要。
ms.date: 09/09/2019
ms.openlocfilehash: cc4ff272a9912d6f2dd8f8ddb1972c7369f980fe
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503456"
---
# <a name="protocol-buffers"></a>プロトコルバッファー

gRPC サービスは、Windows Communication Foundation (WCF) のデータコントラクトと同様に、データを*プロトコルバッファー (Protobuf) メッセージ*として送受信します。 Protobuf は、XML や JSON などの人間が判読できる形式のオーバーヘッドを発生させることなく、マシン用の構造化データを読み書きするための効率的な方法です。

この章では、Protobuf のしくみと、独自の Protobuf メッセージの定義方法について説明します。

## <a name="how-protobuf-works"></a>Protobuf のしくみ

WCF のデータコントラクトを含むほとんどの .NET オブジェクトのシリアル化手法は、リフレクションを使用して実行時にオブジェクト構造を分析することで機能します。 これに対し、ほとんどの Protobuf ライブラリでは、`.proto` ファイルで専用言語 (*プロトコルバッファー言語*) を使用して、構造を事前に定義する必要があります。 コンパイラは、このファイルを使用して、サポートされている任意のプラットフォームのコードを生成します。 サポートされているプラットフォームには、C++.Net、Java、C/、JavaScript などがあります。 

Protobuf コンパイラ (`protoc`) は Google によって管理されますが、代替の実装は使用できます。 生成されたコードは効率的で、データの高速なシリアル化と逆シリアル化のために最適化されています。

Protobuf ワイヤ形式は、バイナリエンコードです。 メッセージを表すために使用されるバイト数を最小限に抑えるために、いくつかの巧妙なテクニックを使用します。 Protobuf を使用するために、バイナリエンコード形式の知識は必要ありません。 ただし、詳細については、「[プロトコルバッファー」 web サイト](https://developers.google.com/protocol-buffers/docs/encoding)を参照してください。

>[!div class="step-by-step"]
>[前へ](why-grpc.md)
>[次へ](protobuf-messages.md)
