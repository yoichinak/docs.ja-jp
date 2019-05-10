---
title: Visual Basic での条件付きコンパイル
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 4698435cb2ab15d16d8a8a898a01a9ffbc4f69c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639803"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic での条件付きコンパイル
*条件付きコンパイル*、他のユーザーは無視されます、特定のプログラムでのコード ブロックは選択的にコンパイルします。  
  
 たとえば、書き込むたい場合があります複数の言語用のアプリケーションをローカライズする必要も、同じプログラミング タスクへのさまざまなアプローチの速度を比較するデバッグ ステートメント可能性があります。 条件付きコンパイル ステートメントの実行時ではなく、コンパイル時に実行するものです。  
  
 条件付きでコンパイルされるようにコードのブロックを指定、`#If...Then...#Else`ディレクティブ。 たとえば、フランス語、ドイツ語を作成する同じから同じアプリケーションのバージョンのソース コード、プラットフォーム固有のコードのセグメントを埋め込む`#If...Then`定義済みの定数を使用してステートメント`FrenchVersion`と`GermanVersion`します。 次の例でどのように。  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 値を設定した場合、`FrenchVersion`に条件付きコンパイル定数`True`コンパイル時にフランス語のバージョンの条件付きのコードをコンパイルします。 値を設定した場合、`GermanVersion`に定数`True`コンパイラはドイツ語版を使用します。 どちらに設定されている場合`True`、最後のコード`Else`ブロックが実行されます。  
  
> [!NOTE]
>  オートコンプリートは、not 関数コードの編集時に、コードは、current branch の一部でない場合は、条件付きコンパイル ディレクティブを使用するには。  
  
## <a name="declaring-conditional-compilation-constants"></a>条件付きコンパイル定数を宣言します。  
 3 つの方法のいずれかでは、条件付きコンパイル定数を設定できます。  
  
- **プロジェクト デザイナー**  
  
- コマンド ライン コンパイラを使用するときに、コマンドラインで  
  
- コードで  
  
 条件付きコンパイル定数は、特殊なスコープを持ち、標準的なコードからアクセスできません。 条件付きコンパイル定数のスコープが設定されている方法によって異なります。 次の表は、上記で説明した 3 つの方法のそれぞれを使用して宣言されている定数のスコープを一覧表示します。  
  
|定数を設定する方法|定数のスコープ|  
|---|---|  
|**プロジェクト デザイナー**|プロジェクト内のすべてのファイルへの公開|  
|コマンド ライン|コマンド ライン コンパイラに渡されるすべてのファイルへの公開|  
|`#Const` コード内のステートメント|宣言されているファイルにプライベート|  
  
|プロジェクト デザイナーで定数を設定するには|  
|---|  
|定数を設定して実行可能ファイルを作成するには、前に、**プロジェクト デザイナー**で提供されている手順に従って[管理プロジェクトおよびソリューションのプロパティ](/visualstudio/ide/managing-project-and-solution-properties)します。|  
  
|コマンドラインで定数を設定するには|  
|---|  
|-を使用して、 **/d**スイッチを次の例のように、条件付きコンパイル定数を入力します。<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     間で必要な空き領域がない、 **/d**スイッチと、最初の定数。 詳細については、次を参照してください。 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)します。<br />     コマンド ラインの宣言で入力した宣言のオーバーライド、**プロジェクト デザイナー**は消去されません。 引数の設定**プロジェクト デザイナー**後続のコンパイルを有効になります。<br />     コード自体で定数を記述する場合はありません、配置場所に関する厳密な規則のスコープは宣言されているモジュール全体であるためです。|  
  
|コードで定数を設定するには|  
|---|  
|-定数を使用するモジュールの宣言ブロックに配置します。 これにより、整理され、読みやすく、コードを維持します。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|---|---|  
|[プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|コードを簡単に読み取りおよびメンテナンスについて説明します。|  
  
## <a name="reference"></a>参照  
 [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
