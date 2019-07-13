---
title: '方法: ポインターを使用してバイトの配列をコピーする - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: d174f51fa1709a70b98473a4dbbad89b9c62c22a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640304"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>方法: ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)

次の例では、ポインターを使って 1 つの配列から別の配列にバイトをコピーします。

この例では、[unsafe](../../language-reference/keywords/unsafe.md) キーワードを使います。このキーワードは、`Copy` メソッドでのポインターの使用を可能にします。 [fixed](../../language-reference/keywords/fixed-statement.md) ステートメントを使って、コピー元とコピー先の配列へのポインターを宣言します。 `fixed` ステートメントを使って、コピー元配列とコピー先配列のメモリ内での位置を "*固定*" し、ガベージ コレクションによって移動されないようにします。 `fixed` ブロックが完了すると、これらの配列のメモリ ブロックは固定解除されます。 この例の `Copy` メソッドは `unsafe` キーワードを使っているので、[-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを指定してコンパイルする必要があります。

この例では、2 番目のアンマネージド ポインターではなくインデックスを使って、両方の配列の要素にアクセスします。 `pSource` と `pTarget` のポインターの宣言を使って配列を固定します。 この機能は、C# 7.3 以降から使用できます。

## <a name="example"></a>例

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [アンセーフ コードとポインター](index.md)
- [-unsafe (C# コンパイラ オプション)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [ガベージ コレクション](../../../standard/garbage-collection/index.md)
