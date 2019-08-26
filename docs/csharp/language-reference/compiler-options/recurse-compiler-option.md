---
title: -recurse (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606743"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (C# コンパイラ オプション)
-recurse オプションを使用すると、指定のディレクトリ (dir) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。  
  
## <a name="syntax"></a>構文  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引数  
 `dir` (省略可能)  
 検索を開始するディレクトリ。 指定しない場合は、プロジェクト ディレクトリから検索されます。  
  
 `file`  
 検索するファイル。 ワイルドカード文字を使用できます。  
  
## <a name="remarks"></a>解説  
 **-recurse** オプションを使用すると、指定のディレクトリ (`dir`) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。  
  
 **-recurse** を使用しなくても、ファイル名にワイルドカードを使用すると、プロジェクト ディレクトリ内で一致するすべてのファイルをコンパイルできます。  
  
 このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。  
  
## <a name="example"></a>例  
 現在のディレクトリ内のすべての C# ファイルをコンパイルするには、次のコードを使用します。  
  
```console  
csc *.cs  
```  
  
 dir1\dir2 ディレクトリおよびそのディレクトリの下の全ディレクトリ内の C# ファイルすべてをコンパイルし、dir2.dll を生成するには、次のコードを使用します。  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](./index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
