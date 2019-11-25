---
title: '@ (応答ファイルの指定)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: c578495bbba0efee79f02da284c7feffb8c12fab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348551"
---
# <a name="-specify-response-file-visual-basic"></a>@ (応答ファイルの指定) (Visual Basic)

Specifies a file that contains compiler options and source-code files to compile.

## <a name="syntax"></a>構文

```console
@response_file
```

## <a name="arguments"></a>引数

`response_file`  
必須です。 A file that lists compiler options or source-code files to compile. Enclose the file name in quotation marks (" ") if it contains a space.

## <a name="remarks"></a>Remarks

The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.

To specify more than one response file in a compilation, specify multiple response-file options, such as the following.

```console
@file1.rsp @file2.rsp
```

In a response file, multiple compiler options and source-code files can appear on one line. A single compiler-option specification must appear on one line (cannot span multiple lines). Response files can have comments that begin with the `#` symbol.

You can combine options specified on the command line with options specified in one or more response files. The compiler processes the command options as it encounters them. Therefore, command-line arguments can override previously listed options in response files. Conversely, options in a response file override options listed previously on the command line or in other response files.

Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file. The Vbc.rsp file is included by default unless the `-noconfig` option is used. For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).

> [!NOTE]
> The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.

## <a name="example"></a>例

The following lines are from a sample response file.

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a>例

The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.

```console
vbc @file1.rsp
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
