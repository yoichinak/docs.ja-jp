---
title: Visual Basic での IEnumerable を実装します。
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 5fc96e1ae3624adc197b5b13029498b9aa90c95e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819503"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>チュートリアル: Visual Basic で IEnumerable(Of T) を実装します。
<xref:System.Collections.Generic.IEnumerable%601>インターフェイスは、一度に 1 つの項目の値のシーケンスを返すことができるクラスによって実装されます。 一度に 1 つの項目がメモリに読み込むデータの完全なセットを扱うことがないことをデータを返すことの利点です。 のみ、データから 1 つの項目を読み込むに十分なメモリを使用する必要があるとします。 実装するクラス、`IEnumerable(T)`インターフェイスで使用できる`For Each`ループまたは LINQ クエリ。  
  
 たとえば、大きなテキスト ファイルを読み取るし、特定の検索条件に一致するファイルからそれぞれの行を返す必要がありますアプリケーションがあるとします。 アプリケーションでは、LINQ クエリを使用して、指定した条件に一致するファイルから行を返します。 LINQ クエリを使用して、ファイルの内容を照会するには、アプリケーションは、配列またはコレクションに、ファイルの内容を読み込む可能性があります。 ただし、配列またはコレクションにファイル全体を読み込むには、必要なよりはるかに多くのメモリが消費します。 LINQ クエリは、検索条件に一致する値のみを返す、列挙可能なクラスを使用して、ファイルの内容を代わりにクエリでした。 いくつかのみを返すクエリを一致する値ははるかに少ないメモリを消費します。  
  
 実装するクラスを作成することができます、<xref:System.Collections.Generic.IEnumerable%601>として列挙可能なデータ ソースのデータを公開するインターフェイス。 実装するクラス、`IEnumerable(T)`インターフェイスを実装する別のクラスが必要になります、<xref:System.Collections.Generic.IEnumerator%601>ソース データを反復処理するインターフェイス。 これら 2 つのクラスを使用すると、順番には、特定の種類のデータ項目を返すことができます。  
  
 このチュートリアルでは、実装するクラスを作成します、`IEnumerable(Of String)`インターフェイスと実装するクラス、`IEnumerator(Of String)`を一度に 1 行ずつテキスト ファイルを読み取るインターフェイス。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>列挙可能なクラスを作成します。  
  
**クラスの列挙可能なプロジェクトを作成します。**

1.  Visual Basic での**ファイル**メニューで、**新規**順にクリックします**プロジェクト**します。

1.  **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。 **[名前]** ボックスに `StreamReaderEnumerable` と入力して、**[OK]** をクリックします。 新しいプロジェクトが表示されます。

1.  **ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。 ファイルの名前を `StreamReaderEnumerable.vb` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `StreamReaderEnumerable` に変更されます。 このクラスが `IEnumerable(Of String)` インターフェイスを実装します。

1.  StreamReaderEnumerable プロジェクトを右クリックし、[**追加**、] をクリックし、**新しい項目の**します。 選択、**クラス**テンプレート。 **名前**ボックスに「 `StreamReaderEnumerator.vb`  をクリック**OK**します。

 このプロジェクトの最初のクラスは列挙可能なクラスであり、実装、`IEnumerable(Of String)`インターフェイス。 このジェネリック インターフェイスを実装して、<xref:System.Collections.IEnumerable>インターフェイスと、このクラスのコンシューマーとして型指定された値にアクセスできることの保証`String`します。  
  
**IEnumerable を実装するコードを追加します。**

1. StreamReaderEnumerable.vb ファイルを開きます。

2. 後の行に`Public Class StreamReaderEnumerable`次を入力し、ENTER キーを押します。

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic では必要なメンバーを持つクラスを自動的に設定する、`IEnumerable(Of String)`インターフェイス。
  
3. この列挙可能なクラスに、一度に 1 行ずつテキスト ファイルから行を読み取ります。 入力パラメーターとしてファイル パスを受け取るパブリック コンス トラクターを公開するクラスには、次のコードを追加します。

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. 実装、<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>のメソッド、`IEnumerable(Of String)`インターフェイスはの新しいインスタンスを返します、`StreamReaderEnumerator`クラス。 実装、`GetEnumerator`のメソッド、`IEnumerable`インターフェイスにできる`Private`のメンバーのみを公開する必要があるため、`IEnumerable(Of String)`インターフェイス。 Visual Basic 用に生成するコードに置き換えます、`GetEnumerator`メソッドを次のコード。

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**IEnumerator を実装するコードを追加します。**

1. StreamReaderEnumerator.vb ファイルを開きます。

2. 後の行に`Public Class StreamReaderEnumerator`次を入力し、ENTER キーを押します。

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic では必要なメンバーを持つクラスを自動的に設定する、`IEnumerator(Of String)`インターフェイス。

3. 列挙子クラスは、テキスト ファイルを開き、ファイルをファイルから行を読み取る I/O を実行します。 クラス ファイルのパスを入力パラメーターとして受け取るパブリック コンス トラクターを公開し、テキスト ファイルを読み取り用に次のコードを追加します。

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current`両方のプロパティ、`IEnumerator(Of String)`と`IEnumerator`インターフェイスとしてテキスト ファイルから現在の項目を返す、`String`します。 実装、`Current`のプロパティ、`IEnumerator`インターフェイスにできる`Private`のメンバーのみを公開する必要があるため、`IEnumerator(Of String)`インターフェイス。 Visual Basic 用に生成するコードに置き換えます、`Current`プロパティを次のコード。

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext`のメソッド、`IEnumerator`インターフェイスが、テキスト ファイルに次の項目に移動し、によって返される値を更新して、`Current`プロパティ。 読み取るには、これ以上項目がある場合、`MoveNext`メソッドを返します。 `False`。 そうしないと、`MoveNext`メソッドを返します。`True`します。 `MoveNext` メソッドに次のコードを追加します。

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset`のメソッド、`IEnumerator`インターフェイスは、テキスト ファイルの先頭を指す反復子に指示し、現在の項目の値を消去します。 `Reset` メソッドに次のコードを追加します。

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose`のメソッド、`IEnumerator`インターフェイス、反復子が破棄される前にすべてのアンマネージ リソースが解放されることを保証します。 によって使用されるファイル ハンドル、`StreamReader`オブジェクトは、アンマネージ リソースし、反復子インスタンスが破棄される前に閉じる必要があります。 Visual Basic 用に生成するコードに置き換えます、`Dispose`メソッドを次のコード。

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>サンプルの反復子を使用

 制御構造を実装するオブジェクトを必要とすると、コード内の列挙可能なクラスを使用できます`IEnumerable`などを`For Next`ループまたは LINQ クエリ。 次の例は、 `StreamReaderEnumerable` LINQ クエリでします。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
