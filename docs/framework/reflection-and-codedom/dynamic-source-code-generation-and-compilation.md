---
title: 動的なソース コードの生成とコンパイル
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8feb94f3d57c25d634bd51b8f41eca42d5e5757a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220310"
---
# <a name="dynamic-source-code-generation-and-compilation"></a>動的なソース コードの生成とコンパイル
.NET Framework には、CodeDOM (Code Document Object Model) と呼ばれるメカニズムが備わっています。CodeDOM を使用すると、ソース コードを出力するプログラム開発者は、レンダリング対象となるコードを表す単一のモデルに基づいて、実行時に複数のプログラミング言語でソース コードを生成することができます。  
  
 ソース コードを表現する CodeDOM 要素は相互にリンクされ、CodeDOM グラフと呼ばれるデータ構造体を形成します。これは、ソース コードの構造をモデル化します。  
  
 `System.CodeDom` 名前空間は、特定のプログラミング言語に依存せずに、ソース コードの論理構造を表すことができる型を定義します。 `System.CodeDom.Compiler` 名前空間は、CodeDOM グラフからソース コードを生成し、サポートされている言語でソース コードのコンパイルを管理する型を定義します。 サポート対象の言語のセットは、コンパイラの販売元および開発者が拡張できます。  
  
 言語に依存しないソース コードのモデル化は、プログラムで複数の言語のプログラム モデルのソース コードを生成する必要がある場合や、対象言語が不明な場合に役立ちます。 たとえば、その言語が CodeDOM でサポートされている場合は、デザイン時に CodeDOM を言語抽象化インターフェイスとして使用し、適切なプログラミング言語でソース コードを生成できます。  
  
 .NET Framework には、<xref:Microsoft.CSharp.CSharpCodeProvider> 用、<xref:Microsoft.JScript.JScriptCodeProvider> 用、および <xref:Microsoft.VisualBasic.VBCodeProvider> 用のコード ジェネレーターとコード コンパイラが用意されています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [CodeDOM の使用方法](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 CodeDOM の一般的な使用方法を説明し、CodeDOM を使って簡単なオブジェクト グラフを構築する例を示します。  
  
 [CodeDOM グラフからのソース コードの生成およびプログラムのコンパイル](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 ソース コードを生成する方法と、生成されたコードを `System.CodeDom.Compiler` 名前空間で定義されているクラスを使って外部コンパイラでコンパイルする方法について説明します。  
  
 [方法: CodeDOM を使用して XML ドキュメント ファイルを作成する](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 CodeDOM を使用して XML ドキュメントのコメント付きのコードを生成する方法、および生成されたコードをコンパイルして XML ドキュメントとして出力する方法について説明します。  
  
 [方法: CodeDOM を使用してクラスを作成する](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 CodeDOM を使用してフィールド、プロパティ、メソッド、コンストラクター、およびエントリ ポイントを持つクラスを生成する方法を説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.CodeDom>  
 共通言語ランタイムを対象とするプログラミング言語のコード要素を表す要素を定義します。  
  
 <xref:System.CodeDom.Compiler>  
 実行時にコードを生成およびコンパイルするためのインターフェイスを定義します。  
  
## <a name="related-sections"></a>関連項目  
 [CodeDOM クイック リファレンス](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))  
 ソース コードの要素を表す CodeDOM 要素を簡単に検索するための方法が用意されています。
