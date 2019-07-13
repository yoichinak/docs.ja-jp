---
title: -pathmap (C# コンパイラ オプション)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 063cee694e8367a86fead2f1258c3cbda5ab7018
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635833"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (C# コンパイラ オプション)

**-pathmap** コンパイラ オプションは、コンパイラによるソース パス名出力への物理パスのマップ方法を指定します。

## <a name="syntax"></a>構文

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>引数

 `path1` 現在の環境でのソース ファイルへの完全なパス

 `sourcePath1` 出力ファイルにおいて `path1` の代わりに使用されるソース パス。

複数のマップされるソース パスを指定するには、コンマで区切ります。

## <a name="remarks"></a>コメント

コンパイラは、次の理由でその出力にソース パスを書き込みます。

1. <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> が省略可能なパラメーターに適用される場合、引数はソース パスに置き換えられます。
1. ソース パスは、PDB ファイルに埋め込まれます。
1. PDB ファイルのパスは、PE (ポータブル実行可能) ファイルに埋め込まれます。

このオプションは、コンパイラが実行されるコンピューター上の各物理パスを、出力ファイルに書き込まれる必要がある対応するパスにマップします。

## <a name="example"></a>例

ディレクトリ **C:\\work\\tests** 内の `t.cs` をコンパイルし、出力ではそのディレクトリを **\publish** にマップします。

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
