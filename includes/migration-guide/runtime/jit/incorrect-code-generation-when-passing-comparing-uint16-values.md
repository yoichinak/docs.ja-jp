---
ms.openlocfilehash: b23909c53b451b4b18bf0ccdf59f51e7c8e3114f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802461"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>UInt16 値を渡して比較する場合にコード生成が正しく行われません

|   |   |
|---|---|
|説明|.NET Framework 4.7 で変更が導入されたため、.NET Framework 4.7 で実行されているアプリケーションの JIT コンパイラによって生成されたコードが 2 つの <code>T:System.UInt16</code> 値を正しく比較しない場合があります。 詳細については、GitHub.com の「[Issue #11508:Silent bad codegen when passing and comparing ushort args](https://github.com/dotnet/coreclr/issues/11508)」 (問題 #11508: ushort の引数を渡して比較する場合のサイレントかつ不適切な codegen) を参照してください。|
|提案される解決策|.NET Framework 4.7 で 16 ビットの符号なし値を比較したときに問題が検出された場合は、.NET Framework 4.7.1 にアップグレードしてください。|
|スコープ|エッジ|
|Version|4.7|
|型|ランタイム|

