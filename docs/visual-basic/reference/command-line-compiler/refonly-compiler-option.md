---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775564"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

**-Refonly**オプションは、コンパイルのプライマリ出力を実装アセンブリではなく参照アセンブリにする必要があることを示します。 `-refonly` パラメーターは、参照アセンブリを実行できない場合に、PDB の出力を暗黙的に無効にします。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>構文

```console
-refonly
```

## <a name="remarks"></a>Remarks

Visual Basic では、バージョン15.3 以降の `-refonly` スイッチがサポートされています。

参照アセンブリは、ライブラリのパブリック API サーフェイスを表すために必要な最小限のメタデータのみを含む、特殊な種類のアセンブリです。 これには、ビルドツールでアセンブリを参照するときに重要なすべてのメンバーの宣言が含まれますが、API コントラクトに影響を与えないプライベートメンバーのすべてのメンバー実装と宣言は除外されます。 詳細については、「.NET での[参照アセンブリ](../../../standard/assembly/reference-assemblies.md)」ガイドを参照してください。

`-refonly` オプションと [`-refout`](refout-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目

- [/refout](refout-compiler-option.md)
- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
