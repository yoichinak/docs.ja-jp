---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612590"
---
# <a name="-quiet"></a>-quiet

コンパイラで構文関連のエラーと警告のコードが表示されないようにします。

## <a name="syntax"></a>構文

```
-quiet
```

## <a name="remarks"></a>Remarks

既定では、`-quiet` は無効です。 コンパイラは、構文に関連するエラーまたは警告を報告、ときにも、ソース コードから行を出力します。 コンパイラ出力を解析するアプリケーションでは、診断のテキストのみを出力するコンパイラのより便利な場合があります。

次の例では、`Module1`出力なしでコンパイル時に、ソース コードを含むエラー`-quiet`します。

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

Output:

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

コンパイルされた`-quiet`コンパイラは、次のオプションのみを出力します。

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> `-quiet`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。

## <a name="example"></a>例

次のコードのコンパイル`T2.vb`構文に関連するコンパイラ診断のコードは表示されません。

```
vbc -quiet t2.vb
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
