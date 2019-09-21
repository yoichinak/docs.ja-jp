---
title: インターフェイスの作成と実装 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 62e301e9eb366d14b58088d3e2cda3b567d17f5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923319"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>チュートリアル: インターフェイスの作成と実装 (Visual Basic)

インターフェイスには、プロパティ、メソッド、およびイベントの特性が記述されていますが、実装の詳細は構造体またはクラスにはありません。  
  
 このチュートリアルでは、インターフェイスを宣言して実装する方法について説明します。  
  
> [!NOTE]
> このチュートリアルでは、ユーザーインターフェイスの作成方法については説明しません。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>インターフェイスを定義するには
  
1. 新しい Visual Basic Windows アプリケーション プロジェクトを開きます。  
  
2. **[プロジェクト]** メニューの **[モジュールの追加]** をクリックして、新しいモジュールをプロジェクトに追加します。  
  
3. 新しいモジュール`Module1.vb`の名前を指定し、 **[追加]** をクリックします。 新しいモジュールのコードが表示されます。  
  
4. ステートメントとステートメントの`TestInterface` `Module1` `Interface TestInterface` `End Module`間に「」と入力し、enter キーを押して、内にという名前のインターフェイスを定義します。 `Module` **コードエディター**によって`Interface`キーワードがインデントさ`End Interface`れ、コードブロックを形成するステートメントが追加されます。  
  
5. `End Interface`ステートメントとステートメントの`Interface`間に次のコードを配置して、インターフェイスのプロパティ、メソッド、およびイベントを定義します。  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>実装

 インターフェイスメンバーの宣言に使用される構文は、クラスメンバーの宣言に使用される構文とは異なることがあります。 この違いは、インターフェイスに実装コードを含めることができないという事実を反映しています。  
  
### <a name="to-implement-the-interface"></a>インターフェイスを実装するには
  
1. という`ImplementationClass`名前のクラスを追加します。 `Module1`そのために`End Interface`は、ステートメントの`End Module`後、ステートメントの前に、enter キーを押します。  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     統合開発環境内で作業している場合、enter キーを押すと`End Class` 、**コードエディター**によって一致するステートメントが提供されます。  
  
2. 次`Implements`のステートメントをに`ImplementationClass`追加します。このステートメントは、クラスが実装するインターフェイスに名前を指定します。  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     クラスまたは構造体の先頭にある他の項目とは別に`Implements`リストされている場合、ステートメントは、クラスまたは構造体がインターフェイスを実装していることを示します。  
  
     統合開発環境内で作業している場合、enter キーを押すと、で`TestInterface`必要なクラスメンバーが**コードエディター**に実装されます。次の手順は省略できます。  
  
3. 統合開発環境で作業していない場合は、インターフェイス`MyInterface`のすべてのメンバーを実装する必要があります。 `ImplementationClass` `Event1`、 、および`Prop1`を実装するには、に次のコードを追加します。 `Method1`  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     ステートメント`Implements`は、実装されているインターフェイスとインターフェイスメンバーの名前を記述します。  
  
4. プロパティ値を格納`Prop1`したクラスにプライベートフィールドを追加して、の定義を完了します。  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     プロパティ get アクセサー `pval`からの値を返します。  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     プロパティセットアクセサーで`pval`の値を設定します。  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. 次のコードを`Method1`追加して、の定義を完了します。  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>インターフェイスの実装をテストするには
  
1. **ソリューションエクスプローラー**でプロジェクトのスタートアップフォームを右クリックし、 **[コードの表示]** をクリックします。 エディターに、スタートアップフォームのクラスが表示されます。 既定では、スタートアップフォームが呼び出さ`Form1`れます。  
  
2. クラスに次`testInstance`のフィールドを追加します。 `Form1`  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     とし`testInstance` `WithEvents`て宣言する`Form1`ことで、クラスはそのイベントを処理できます。  
  
3. 次のイベントハンドラーを`Form1`クラスに追加して、によって`testInstance`発生したイベントを処理します。  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. クラスにという`Test`名前のサブルーチンを追加して、実装クラスをテストします。 `Form1`  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     この`Test`プロシージャは、を実装`MyInterface`するクラスのインスタンスを作成し、そのインスタンス`testInstance`をフィールドに割り当て、プロパティを設定し、インターフェイスを介してメソッドを実行します。  
  
5. スタートアップフォームの`Form1 Load`プロシージャから`Test`プロシージャを呼び出すコードを追加します。  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. F5 キー `Test`を押してプロシージャを実行します。 "Prop1 が9に設定されました" というメッセージが表示されます。 [OK] をクリックすると、"Method1 の X パラメーターは 5" というメッセージが表示されます。 [OK] をクリックすると、"イベントをキャッチしたイベントハンドラー" というメッセージが表示されます。  
  
## <a name="see-also"></a>関連項目

- [Implements ステートメント](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [インターフェイス](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface ステートメント](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)
