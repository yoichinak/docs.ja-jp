---
title: ソース行、ファイル、およびパスの識別子
description: 組み込み F# 識別子の値を使用するソース行番号、ディレクトリ、およびファイル名をコードにアクセスできるようにする方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 4b145fe1fe20e3d7f868558e33bab26204fb0125
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663623"
---
# <a name="source-line-file-and-path-identifiers"></a>ソース行、ファイル、およびパスの識別子

識別子`__LINE__`、`__SOURCE_DIRECTORY__`と`__SOURCE_FILE__`は、コードのソース行番号、ディレクトリおよびファイル名にアクセスするための組み込みの値です。

## <a name="syntax"></a>構文

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Remarks

これらの値の各種類には`string`します。

次の表は、ソース行、ファイル、および F# で使用できるパスの識別子を示します。 これらの識別子でないプリプロセッサ マクロこれらは、コンパイラによって認識される組み込みの値です。

|事前定義の識別子|説明|
|---------------------|-----------|
|`__LINE__`|現在の行番号に評価を検討して`#line`ディレクティブ。|
|`__SOURCE_DIRECTORY__`|ソース ディレクトリの現在の完全なパスに評価を検討して`#line`ディレクティブ。|
|`__SOURCE_FILE__`|現在のソース ファイル名と、そのパスに評価を検討して`#line`ディレクティブ。|

詳細については、`#line`ディレクティブを参照してください[コンパイラ ディレクティブ](compiler-directives.md)します。

## <a name="example"></a>例

次のコード例では、これらの値の使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Output:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>関連項目

- [コンパイラ ディレクティブ](compiler-directives.md)
- [F# 言語リファレンス](index.md)
