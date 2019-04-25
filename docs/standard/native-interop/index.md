---
title: ネイティブ相互運用性 - .NET
description: .Net のネイティブ コンポーネントとやり取りする方法を説明します。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 29aacc9210b4103f379b7776c36fc3c29b9e6dec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973559"
---
# <a name="native-interoperability"></a>ネイティブ相互運用性

次の各記事では、.NET での "ネイティブ相互運用" のさまざまな方法を示しています。

ネイティブ コードの呼び出しが必要になる理由としては、次のようなものがあります。

* オペレーティング システムに付属している大量の API が、マネージド クラス ライブラリに存在していない。 この主な例には、ハードウェアやオペレーティング システムの管理機能へのアクセスがあります。
* C スタイル ABI (ネイティブ ABI) を持つか生成できる他のコンポーネントと通信する。たとえば、[Java ネイティブ インターフェイス (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) を介して公開されている Java コードや、ネイティブ コンポーネントを生成できるその他のマネージド言語です。
* Windows では、インストールされるソフトウェアのほとんどが (たとえば Microsoft Office スイート)、COM コンポーネントを登録します。このコンポーネントは、そのソフトウェアのプログラムを表すものであり、開発者による自動化や使用が可能になります。 これも、ネイティブ相互運用性を必要とします。

開発者がネイティブ コンポーネントとやり取りすることが必要になる状況やシナリオは、上記の一覧に示すものがすべてではありません。 たとえば、.NET クラス ライブラリは、ネイティブ相互運用性サポートを使用して、コンソールのサポートと操作、ファイル システムのアクセスなど、そのかなりの数の API を実装しています。 ただし、必要であればできる、ということを覚えておくことが重要です。

> [!NOTE]
> このセクションのほとんどの例は、.NET Core でサポートされる 3 つのプラットフォームすべて (Windows、Linux、macOS) について提示しています。 ただし、短い解説的な例については、Windows ファイル名と拡張子 (つまり、ライブラリの場合は "dll") を使用する 1 つのサンプルだけを示します。 その機能が Linux や macOS で使用できないというわけではなく、単に便宜上のためにそうしています。

## <a name="see-also"></a>関連項目

- [プラットフォーム呼び出し (P/Invoke)](pinvoke.md)
- [型のマーシャリング](type-marshalling.md)
- [ネイティブ相互運用性のベスト プラクティス](best-practices.md)
