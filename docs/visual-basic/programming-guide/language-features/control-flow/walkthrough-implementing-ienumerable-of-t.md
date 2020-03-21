---
title: IEnumerable の実装
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266912"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>チュートリアル: Visual Basic での IEnumerable(Of T) の実装
インターフェイス<xref:System.Collections.Generic.IEnumerable%601>は、一度に 1 項目ずつ値のシーケンスを返すことができるクラスによって実装されます。 一度に 1 つの項目でデータを返す利点は、データの完全なセットをメモリに読み込んで作業する必要がなさ、ということです。 データから 1 つの項目を読み込むために十分なメモリを使用するだけで済みます。 インターフェイスを実装する`IEnumerable(T)`クラスは、ループまたは`For Each`LINQ クエリで使用できます。  
  
 たとえば、大きなテキスト ファイルを読み取り、特定の検索条件に一致するファイルから各行を返す必要があるアプリケーションを考えてみます。 アプリケーションは、指定された条件に一致するファイルから行を返すために LINQ クエリを使用します。 LINQ クエリを使用してファイルの内容を照会するために、アプリケーションはファイルの内容を配列またはコレクションに読み込むことができます。 ただし、ファイル全体を配列またはコレクションに読み込むと、必要なメモリよりもはるかに多くのメモリが消費されます。 LINQ クエリは、列挙可能なクラスを使用してファイルの内容をクエリし、検索条件に一致する値のみを返すことができます。 一致する値を少数しか返さなクエリでは、消費するメモリの量が非常に少なくなります。  
  
 インターフェイスを実装するクラスを作成して、<xref:System.Collections.Generic.IEnumerable%601>ソース データを列挙可能なデータとして公開できます。 `IEnumerable(T)`インターフェイスを実装するクラスには、ソース データを反復処理するインターフェイス<xref:System.Collections.Generic.IEnumerator%601>を実装する別のクラスが必要です。 これら 2 つのクラスを使用すると、データの項目を特定の型として順番に返します。  
  
 このチュートリアルでは、`IEnumerable(Of String)`インターフェイスを実装するクラスと、テキスト ファイルを一度に 1`IEnumerator(Of String)`行ずつ読み取るインターフェイスを実装するクラスを作成します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>列挙可能なクラスの作成  
  
**列挙可能なクラス プロジェクトを作成します。**

1. Visual Basic の [**ファイル**] メニューの [**新規作成**] をポイントし、[**プロジェクト**] をクリックします。

1. **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。 **[名前]** ボックスに `StreamReaderEnumerable` と入力して、**[OK]** をクリックします。 新しいプロジェクトが表示されます。

1. **ソリューション エクスプローラ**で、Class1.vb ファイルを右クリックし、[**名前の変更**] をクリックします。 ファイルの名前を `StreamReaderEnumerable.vb` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `StreamReaderEnumerable` に変更されます。 このクラスが `IEnumerable(Of String)` インターフェイスを実装します。

1. プロジェクトを右クリックし、[**追加**] をポイントして、[**新しい項目**] をクリックします。 **[クラス**] テンプレートを選択します。 **[名前]** ボックスに「`StreamReaderEnumerator.vb`」と入力し、**[OK]** をクリックします。

 このプロジェクトの最初のクラスは列挙可能なクラスであり、インターフェイスを実装`IEnumerable(Of String)`します。 このジェネリック インターフェイスはインターフェイス<xref:System.Collections.IEnumerable>を実装し、このクラスのコンシューマーが 型指定された値に`String`アクセスできることを保証します。  
  
**IEnumerable を実装するコードを追加します。**

1. ファイルを開きます。

2. の後`Public Class StreamReaderEnumerable`の行に、次のコマンドを入力し、Enter キーを押します。

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic では、インターフェイスに必要なメンバーが自動的にクラス`IEnumerable(Of String)`に設定されます。
  
3. この列挙可能なクラスは、テキスト ファイルから一度に 1 行ずつ行を読み取ります。 次のコードをクラスに追加して、ファイル パスを入力パラメーターとして受け取るパブリック コンストラクターを公開します。

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. インターフェイスのメソッドの<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>実装は`IEnumerable(Of String)`、クラスの新しいインスタンスを`StreamReaderEnumerator`返します。 インターフェイスの`GetEnumerator`メンバーのみを公開する必要があるため、インターフェイスの`Private`メソッドの`IEnumerable(Of String)`実装を行うことができます。 `IEnumerable` メソッドに対して生成されたコードを次`GetEnumerator`のコードに置き換えます。

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**IEnumerator を実装するコードを追加します。**

1. ファイルを開きます。

2. の後`Public Class StreamReaderEnumerator`の行に、次のコマンドを入力し、Enter キーを押します。

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic では、インターフェイスに必要なメンバーが自動的にクラス`IEnumerator(Of String)`に設定されます。

3. 列挙子クラスは、テキスト ファイルを開き、ファイル I/O を実行してファイルから行を読み取ります。 次のコードをクラスに追加して、ファイル パスを入力パラメーターとして受け取るパブリック コンストラクターを公開し、読み取り用にテキスト ファイルを開きます。

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. インターフェイス`Current`と インターフェイス`IEnumerator(Of String)``IEnumerator`の両方のプロパティは、テキスト ファイルから現在のアイテム`String`を . インターフェイスの`Current`メンバーのみを公開する必要があるため、インターフェイスの`Private`プロパティの`IEnumerator(Of String)`実装を行うことができます。 `IEnumerator` プロパティに対して生成されたコードを次`Current`のコードに置き換えます。

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. インターフェイス`MoveNext`の`IEnumerator`メソッドは、テキスト ファイル内の次の項目に移動し、プロパティによって返される値を`Current`更新します。 読み取る項目がなくなった場合、メソッド`MoveNext`は返`False`します。それ以外`MoveNext`の場合`True`、メソッドは を返します。 `MoveNext` メソッドに次のコードを追加します。

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. インターフェイス`Reset`の`IEnumerator`メソッドは、テキスト ファイルの先頭を指し示す反復器を指示し、現在の項目の値をクリアします。 `Reset` メソッドに次のコードを追加します。

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. インターフェイス`Dispose`の`IEnumerator`メソッドは、反復器が破棄される前にすべてのアンマネージ リソースが解放されることを保証します。 `StreamReader`オブジェクトによって使用されるファイル ハンドルはアンマネージ リソースであり、反復処理インスタンスが破棄される前に閉じる必要があります。 メソッドに対して生成されたコードを`Dispose`次のコードに置き換えます。

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>サンプル反復器の使用

 コード内で列挙可能なクラスを使用し、ループや LINQ クエリなどの`IEnumerable`を実装するオブジェクトを必要とするコントロール構造を使用できます。 `For Next` 次の例は、LINQ`StreamReaderEnumerable`クエリの例です。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
