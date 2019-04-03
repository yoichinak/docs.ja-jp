---
title: /refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: f2cdd228d8ce1912abbbe888c29c42f29299ebba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832737"
---
# <a name="-refout-visual-basic"></a>/refout (Visual Basic)

**-refout** オプションは、参照アセンブリを出力するファイル パスを指定します。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>構文

```console
-refout:filepath
```

## <a name="arguments"></a>引数

 `filepath` パスと、参照アセンブリのファイル名。 一般にプライマリ アセンブリのサブ フォルダーでなければなりません。 (MSBuild で使用される) 推奨規則は、プライマリ アセンブリに相対する "ref/" サブ フォルダー内に参照アセンブリを配置することです。 すべてのフォルダーで`filepath`; が存在する必要がありますに、コンパイラは作成されません。 

## <a name="remarks"></a>Remarks

Visual Basic は、`-refout`バージョン 15.3 以降を切り替えます。

参照アセンブリは、実装コードではなくメタデータが含まれているメタデータのみアセンブリです。 匿名型を除くすべての型およびメンバーの情報が含まれます。 1 つに、メソッドの本体が置き換えられます`throw null`ステートメント。 使用する理由`throw null`(本体なし) ではなく、メソッド本体が PEVerify を実行して (したがって、メタデータの完全性を検証する) を渡すようにします。

参照アセンブリは、アセンブリ レベル[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)属性。 この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。 この属性により、ランタイムの実行の参照アセンブリの読み込みが拒否 (ただしリフレクション専用コンテキストに読み込まれていることがあります)。 アセンブリにリフレクションするツールは、リフレクション専用として参照アセンブリが読み込まれることを確認する必要があります。それ以外の場合、ランタイム、<xref:System.BadImageFormatException>します。

`-refout` オプションと [`-refonly`](refonly-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目

- [/refonly](refonly-compiler-option.md)
- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
