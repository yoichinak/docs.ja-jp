---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775550"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**-refout** オプションは、参照アセンブリを出力するファイル パスを指定します。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>構文

```console
-refout:filepath
```

## <a name="arguments"></a>引数

`filepath`  
参照アセンブリのパスとファイル名。 通常、プライマリアセンブリのサブフォルダーに存在する必要があります。 (MSBuild で使用される) 推奨規則は、プライマリ アセンブリに相対する "ref/" サブ フォルダー内に参照アセンブリを配置することです。 @No__t_0 内のすべてのフォルダーが存在している必要があります。コンパイラでは、これらは作成されません。

## <a name="remarks"></a>Remarks

Visual Basic では、バージョン15.3 以降の `-refout` スイッチがサポートされています。

参照アセンブリは、ライブラリのパブリック API サーフェイスを表すために必要な最小限のメタデータのみを含む、特殊な種類のアセンブリです。 これには、ビルドツールでアセンブリを参照するときに重要なすべてのメンバーの宣言が含まれますが、API コントラクトに影響を与えないプライベートメンバーのすべてのメンバー実装と宣言は除外されます。 詳細については、「.NET での[参照アセンブリ](../../../standard/assembly/reference-assemblies.md)」ガイドを参照してください。

`-refout` オプションと [`-refonly`](refonly-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目

- [/refonly](refonly-compiler-option.md)
- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
