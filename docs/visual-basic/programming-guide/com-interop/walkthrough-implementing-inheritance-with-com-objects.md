---
title: 'チュートリアル: (Visual Basic) の COM オブジェクトによる継承の実装'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: ee7258a78ad0a434bfad08eebd596a8b889e2304
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826172"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>チュートリアル: (Visual Basic) の COM オブジェクトによる継承の実装
Visual Basic クラスを派生する`Public`、以前のバージョンの Visual Basic で作成されたものであっても、COM オブジェクトのクラス。 COM オブジェクトから継承されたクラスのメソッドとプロパティをオーバーライドまたはプロパティと同様にオーバー ロード、およびその他の任意の基本クラスのメソッドをオーバーライドまたはオーバー ロードできます。 COM オブジェクトからの継承は、再コンパイルしたくない既存のクラス ライブラリがある場合に便利です。  
  
 次の手順では、Visual Basic 6.0 を使用して、クラスを含む COM オブジェクトを作成し、基本クラスとして使用する方法を示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>このチュートリアルで使用されている COM オブジェクトを構築するには  
  
1.  Visual Basic 6.0 では、新しい ActiveX DLL プロジェクトを開きます。 という名前のプロジェクト`Project1`が作成されます。 という名前のクラスが`Class1`します。  
  
2.  **プロジェクト エクスプ ローラー**を右クリックして**Project1**、 をクリックし、 **Project1 プロパティ**します。 **プロジェクト プロパティ** ダイアログ ボックスが表示されます。  
  
3.  **全般**のタブ、**プロジェクトのプロパティ** ダイアログ ボックスで、プロジェクトの名前を入力して変更`ComObject1`で、**プロジェクト名**フィールド。  
  
4.  **プロジェクト エクスプ ローラー**を右クリックして`Class1`、 をクリックし、**プロパティ**します。 **プロパティ**クラスのウィンドウが表示されます。  
  
5.  変更、`Name`プロパティを`MathFunctions`します。  
  
6.  **プロジェクト エクスプ ローラー**を右クリックして`MathFunctions`、 をクリックし、**コードの表示**します。 **コード エディター**が表示されます。  
  
7.  プロパティ値を保持するローカル変数を追加します。  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  プロパティ追加`Let`プロパティと`Get`プロパティ プロシージャ。  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. 関数を追加します。  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 作成し、クリックして、COM オブジェクトを登録**ように ComObject1.dll**上、**ファイル**メニュー。  
  
    > [!NOTE]
    >  COM オブジェクトとして Visual Basic で作成したクラスを公開することも、本当の COM オブジェクトでないし、このチュートリアルでは使用できません。 詳細については、次を参照してください。 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)します。  
  
## <a name="interop-assemblies"></a>相互運用機能アセンブリ  
 次の手順では、(COM オブジェクト) などのアンマネージ コードと Visual Studio を使用してマネージ コード間のブリッジとして機能する、相互運用機能アセンブリを作成します。 Visual Basic によって作成される相互運用機能アセンブリは、COM オブジェクトなどの操作の詳細の多くを処理*相互運用マーシャ リング*、パッケージ パラメーターと戻り値を同等のデータの処理の種類に移動し、COM オブジェクト。 Visual Basic アプリケーション内の参照は、実際の COM オブジェクトではなく、相互運用機能アセンブリを指します。  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Visual Basic 2005 およびそれ以降のバージョンで COM オブジェクトを使用するには  
  
1.  新しい Visual Basic Windows アプリケーション プロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
     **[参照の追加]** ダイアログ ボックスが表示されます。  
  
3.  **COM**  タブで、ダブルクリックして`ComObject1`で、**コンポーネント名**を一覧表示し、をクリックして**ok**します。  
  
4.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
5.  **テンプレート**ウィンドウで、をクリックして**クラス**します。  
  
     既定のファイル名、`Class1.vb`に表示されます、**名前**フィールド。 MathClass.vb をクリックして、このフィールドを変更**追加**します。 これは、という名前のクラスを作成します。 `MathClass`、し、そのコードを表示します。  
  
6.  先頭に次のコードを追加`MathClass`COM クラスから継承するようにします。  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7.  次のコードを追加することで、基底クラスのパブリック メソッドをオーバー ロード`MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8.  次のコードを追加することで、継承されたクラスを拡張`MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 新しいクラスは COM オブジェクトの基底クラスのプロパティを継承するには、メソッドをオーバー ロードおよびクラスを拡張する新しいメソッドを定義します。  
  
#### <a name="to-test-the-inherited-class"></a>継承されたクラスをテストするには  
  
1.  スタートアップ フォームにボタンを追加しをダブルクリックして、そのコードを表示します。  
  
2.  ボタンの`Click`イベント ハンドラー プロシージャのインスタンスを作成する次のコードを追加`MathClass`オーバー ロードされたメソッドを呼び出します。  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3.  F5 キーを押してプロジェクトを実行します。  
  
 フォーム上のボタンをクリックすると、`AddNumbers`メソッドが呼び出された最初`Short`データ型の数字、および Visual Basic は、基底クラスから、適切なメソッドを選択します。 2 番目の呼び出し`AddNumbers`はからオーバー ロード メソッドに送られます`MathClass`します。 3 番目の呼び出しの呼び出し、`SubtractNumbers`メソッドで、クラスを拡張します。 基本クラスのプロパティが設定され、値が表示されます。  
  
## <a name="next-steps"></a>次の手順  
 お気付きかもしれませんが、オーバー ロードされた`AddNumbers`させるデータ型は COM オブジェクトの基本クラスから継承されたメソッドとして同じ関数が表示されます。 これは、引数と、基底クラス メソッドのパラメーターは、Visual Basic 6.0 で 16 ビット整数として定義されますが、型の 16 ビット整数として公開されるため`Short`Visual Basic のそれ以降のバージョン。 新しい関数は、32 ビットの整数を受け取り、基底クラスの関数をオーバー ロードします。  
  
 COM オブジェクトを使用する場合は、パラメーターのサイズとデータの型を確認することを確認します。 など、Visual Basic 6.0 のコレクション オブジェクトを引数として受け取る COM オブジェクトを使用しているときに、以降のバージョンの Visual Basic からコレクションを提供できません。  
  
 プロパティとメソッドが COM クラスから継承された上書きできます。 つまり、ローカルのプロパティまたはプロパティを置換するメソッドまたは COM の基本クラスから継承されたメソッドを宣言することができます。 継承された COM プロパティをオーバーライドするための規則は、他のプロパティと、次の例外を持つメソッドをオーバーライドするためのルールに似ています。  
  
-   任意のプロパティまたは COM クラスから継承されたメソッドをオーバーライドする場合は、他のすべての継承されたプロパティとメソッドをオーバーライドする必要があります。  
  
-   プロパティを使用する`ByRef`パラメーターをオーバーライドすることはできません。  
  
## <a name="see-also"></a>関連項目

- [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
