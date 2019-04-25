---
title: '方法: アセンブリの完全修飾名を特定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a4ef1f5bde121d5773925437307b2749aa7282
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097539"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a>方法: アセンブリの完全修飾名を特定する
グローバル アセンブリ キャッシュ内のアセンブリの完全修飾名を検出するには、グローバル アセンブリ キャッシュ ツール ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)) を使用します。 「[方法:グローバル アセンブリ キャッシュの内容を表示する](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)」をご覧ください。  
  
 グローバル アセンブリ キャッシュにないアセンブリについては、複数の方法で完全修飾アセンブリ名を取得できます。コードを使用しコンソールや変数に情報を出力したり、[Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して完全修飾名を含むアセンブリのメタデータを調べたりできます。  
  
-   アセンブリがアプリケーションによって既に読み込まれている場合、<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> プロパティの値を取得して、完全修飾名を取得できます。 この方法を使用して、アセンブリが GAC 内にあるかどうかを判別できます。 具体的な例を次に示します。  
  
-   アセンブリのファイル システム パスがわかっている場合は、(`Shared` Visual Basic で) 静的 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> メソッドを呼び出して、完全修飾アセンブリ名を取得できます。 単純な例を次に示します。  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   [Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリのメタデータを使用できます。これには完全修飾名が含まれています。  
  
 バージョン、カルチャ、アセンブリ名などのアセンブリ属性の設定の詳細については、「[アセンブリ属性の設定](../../../docs/framework/app-domains/set-assembly-attributes.md)」を参照してください。 アセンブリに厳密な名前を指定する方法の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)」を参照してください。  
  
## <a name="example"></a>例  
 指定したクラスを含むアセンブリの完全限定名をコンソールに表示するコード例を次に示します。 アプリによって既に読み込まれているアセンブリの名前を取得するので、アセンブリが GAC 内にあるかどうかは重要ではありません。  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [アセンブリ名](../../../docs/framework/app-domains/assembly-names.md)
- [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)
- [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)
- [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
