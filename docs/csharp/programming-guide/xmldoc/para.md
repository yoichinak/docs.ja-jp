---
title: <para> - C# プログラミング ガイド
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: b2740370106ce5b2812acbea212354ebea1f0e34
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793420"
---
# <a name="para-c-programming-guide"></a>\<para> (C# プログラミング ガイド)

## <a name="syntax"></a>構文

```xml
<para>content</para>
```

## <a name="parameters"></a>パラメーター

- `content`

  段落のテキストです。

## <a name="remarks"></a>Remarks

\<para> タグは、[\<summary>](./summary.md)、[\<remarks>](./remarks.md)、または [\<returns>](./returns.md) などのタグ内で使用し、テキストに構造を追加することができます。

コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

\<para> の使用例については、「[\<summary>](./summary.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)
