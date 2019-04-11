---
title: 作成するインターフェイスと実装 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: faed4d3c9498938e022daf821dd0aefbcbcf2e8d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322031"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>チュートリアル: 作成するインターフェイスと実装 (Visual Basic)

インターフェイスは、プロパティ、メソッド、およびイベントの特性を記述が最大構造体またはクラスの実装の詳細のままにします。  
  
 このチュートリアルでは、宣言およびインターフェイスを実装する方法を示します。  
  
> [!NOTE]
>  このチュートリアルでは、ユーザー インターフェイスを作成する方法についての情報を提供しません。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>インターフェイスを定義するには
  
1. 新しい Visual Basic Windows アプリケーション プロジェクトを開きます。  
  
2. 新しいモジュールをクリックして、プロジェクトに追加**モジュールの追加**上、**プロジェクト**メニュー。  
  
3. 新しいモジュールの名前を付けます`Module1.vb`クリック**追加**。 新しいモジュールのコードが表示されます。  
  
4. という名前のインターフェイスを定義`TestInterface`内`Module1`」と入力して`Interface TestInterface`間、`Module`と`End Module`ステートメント、およびし、ENTER キーを押します。 **コード エディター**インデント、`Interface`キーワードを追加し、`End Interface`コード ブロックを形成するステートメント。  
  
5. 間に次のコードを配置することで、プロパティ、メソッド、およびインターフェイスのイベントを定義、`Interface`と`End Interface`ステートメント。  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>実装

 インターフェイス メンバーを宣言するために使用する構文はクラス メンバーを宣言するために使用する構文と異なることに注意してください可能性があります。 この違いは、インターフェイスが実装コードを含めることはできませんという事実を反映します。  
  
### <a name="to-implement-the-interface"></a>インターフェイスを実装するには
  
1. という名前のクラスを追加`ImplementationClass`次のステートメントを追加して`Module1`後に、`End Interface`ステートメントする前に、`End Module`ステートメント、および ENTER を押してします。  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     統合開発環境内で作業している場合、**コード エディター**提供、一致する`End Class`ENTER キーを押したときのステートメント。  
  
2. 次の追加`Implements`ステートメントを`ImplementationClass`クラス、インターフェイスの名前を実装します。  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     クラスまたは構造体の上部にある他の項目とは別に表示されている場合、`Implements`ステートメントでは、クラスまたは構造体がインターフェイスを実装することを示します。  
  
     統合開発環境内で作業している場合、**コード エディター**で必要なクラス メンバーを実装して`TestInterface`、ENTER キーを押すし、次の手順をスキップすることができます。  
  
3. 統合開発環境内で動作していない場合は、インターフェイスのすべてのメンバーを実装する必要があります`MyInterface`します。 次のコードを追加`ImplementationClass`を実装する`Event1`、 `Method1`、および`Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements`ステートメント インターフェイスおよび実装するインターフェイス メンバーの名前します。  
  
4. 定義が完了`Prop1`プロパティ値を格納するクラスにプライベート フィールドを追加することで。  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     値を返す、`pval`プロパティからアクセサーを取得します。  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     値を設定`pval`プロパティ アクセサーを設定します。  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. 定義が完了`Method1`次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>インターフェイスの実装をテストするには
  
1. プロジェクトのスタートアップ フォームを右クリックし、**ソリューション エクスプ ローラー**、 をクリック**コードの表示**します。 エディターには、スタートアップ フォームのクラスが表示されます。 既定では、スタートアップ フォームと呼ばれる`Form1`します。  
  
2. 次の追加`testInstance`フィールドを`Form1`クラス。  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     宣言することで`testInstance`として`WithEvents`、`Form1`クラスは、そのイベントを処理できます。  
  
3. 次のイベント ハンドラーを追加、`Form1`によって生成されるイベントを処理するクラスを`testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. という名前のサブルーチンを追加`Test`を`Form1`実装クラスをテストするクラス。  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test`プロシージャは、実装するクラスのインスタンスを作成します。 `MyInterface`、そのインスタンスを割り当てます、`testInstance`フィールド、プロパティの設定およびインターフェイスを通じたメソッドを実行します。  
  
5. 呼び出すコードを追加、`Test`プロシージャから、`Form1 Load`スタートアップ フォームの手順。  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. 実行、 `Test` f5 キーを押してプロシージャ。 メッセージ"Prop1 が 9 に設定"が表示されます。 クリックした後、メッセージ"Method1 の X パラメーター is 5"が表示されます。 [Ok] をクリックして、「イベント ハンドラーが、イベントが発生しました」のメッセージが表示されます。  
  
## <a name="see-also"></a>関連項目

- [Implements ステートメント](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [インターフェイス](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface ステートメント](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)
