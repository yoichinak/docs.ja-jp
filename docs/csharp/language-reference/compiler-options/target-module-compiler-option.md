---
title: -target:module (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 89139867cb0a207dbe82168015629fcb9e2fa6eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601897"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:module (C# コンパイラ オプション)
このオプションでは、コンパイラはアセンブリ マニフェストを生成しません。  
  
## <a name="syntax"></a>構文  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>コメント  
 既定では、このオプションを使用してコンパイルすることによって作成された出力ファイルに、.netmodule という拡張子が付きます。  
  
 アセンブリ マニフェストのないファイルは、.NET Framework 共通言語ランタイムで読み込むことができません。 ただし、このようなファイルは、[-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) を使用して、アセンブリのアセンブリ マニフェストに組み込むことができます。  
  
 複数のモジュールが 1 回のコンパイルで作成される場合、あるモジュールの [internal](../../../csharp/language-reference/keywords/internal.md) 型をコンパイル中に別のモジュールで使用することができます。 あるモジュールのコードが別のモジュールの `internal` 型を参照する場合は、**-addmodule** を使用して、両方のモジュールをアセンブリ マニフェストに組み込む必要があります。  
  
 Visual Studio 開発環境では、モジュールの作成はサポートされていません。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、`in.netmodule` を作成するには、次のコードを使用します。  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>関連項目

- [-target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
