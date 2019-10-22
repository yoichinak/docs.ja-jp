---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582873"
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

参照アセンブリはメタデータのみを格納するアセンブリであり、実装コードは含まれません。 これには、匿名型以外のすべての型とメンバーの情報が含まれます。 これらのメソッド本体は、1つの `throw null` ステートメントに置き換えられます。 (本文なしではなく) `throw null` メソッド本体を使用する理由は、PEVerify が実行されて合格 (したがって、メタデータの完全性を検証する) ことができるようにするためです。

参照アセンブリには、アセンブリレベルの[referenceassembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)属性が含まれます。 この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。 この属性により、ランタイムは参照アセンブリの読み込みを拒否します (リフレクションのみのコンテキストに読み込むこともできます)。 アセンブリに反映されるツールは、リフレクションのみで参照アセンブリを読み込む必要があります。それ以外の場合、ランタイムは <xref:System.BadImageFormatException> をスローします。

`-refout` オプションと [`-refonly`](refonly-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目

- [/refonly](refonly-compiler-option.md)
- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
