---
title: ソース行、ファイル、およびパスの識別子
description: 組み込みのF#識別子値を使用して、コード内のソース行番号、ディレクトリ、およびファイル名にアクセスできるようにする方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216751"
---
# <a name="source-line-file-and-path-identifiers"></a>ソース行、ファイル、およびパスの識別子

識別子`__LINE__` `__SOURCE_DIRECTORY__`とは、コード内のソース行番号、ディレクトリ、およびファイル名にアクセスできるようにする組み込みの値です。`__SOURCE_FILE__`

## <a name="syntax"></a>構文

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>コメント

これらの各値には`string`型があります。

次の表は、でF#使用できるソース行、ファイル、およびパスの識別子をまとめたものです。 これらの識別子はプリプロセッサマクロではありません。これらは、コンパイラによって認識される組み込みの値です。

|定義済み識別子|説明|
|---------------------|-----------|
|`__LINE__`|ディレクティブを考慮`#line`して、現在の行番号に評価されます。|
|`__SOURCE_DIRECTORY__`|ディレクティブを考慮`#line`して、ソースディレクトリの現在の完全パスに評価されます。|
|`__SOURCE_FILE__`|ディレクティブを考慮`#line`して、パスを除いた現在のソースファイル名に評価されます。|

ディレクティブの`#line`詳細については、「[コンパイラディレクティブ](compiler-directives.md)」を参照してください。

## <a name="example"></a>例

これらの値の使用方法を次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Output:

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>関連項目

- [コンパイラ ディレクティブ](compiler-directives.md)
- [F# 言語リファレンス](index.md)
