---
title: クラスを定義する (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: 3129824f6e4047420c422503cc366a1c8d28b7e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61865296"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>チュートリアル: クラスを定義する (Visual Basic)

このチュートリアルでは、オブジェクトを作成し使用するクラスを定義する方法を示します。 また、プロパティとメソッドを新しいクラスに追加する方法を示しますされ、オブジェクトを初期化する方法を示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>クラスを定義するには
  
1. クリックしてプロジェクトを作成**新しいプロジェクト**上、**ファイル**メニュー。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2. Windows アプリケーションを新しいプロジェクトを表示する Visual Basic プロジェクト テンプレートの一覧から選択します。  
  
3. クリックして、プロジェクトに新しいクラスを追加**クラスの追加**上、**プロジェクト**メニュー。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
4. 選択、**クラス**テンプレート。  
  
5. 新しいクラスの名前`UserNameInfo.vb`、 をクリックし、**追加**新しいクラスのコードを表示します。  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Visual Basic を使用する**コード エディター** 」と入力して、スタートアップ フォームにクラスを追加する、`Class`キーワードの後に、新しいクラスの名前。 **コード エディター** 、対応する提供`End Class`するステートメント。  
  
6. 間に次のコードを追加することで、クラスのプライベート フィールドを定義、`Class`と`End Class`ステートメント。  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     フィールドとして宣言する`Private`クラス内でのみ使用できることを意味します。 利用できるフィールドからクラスの外部でなどのアクセス修飾子を使用して`Public`のアクセスを提供します。 詳細については、[ Visual Basic のアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
7. 次のコードを追加することで、クラスのプロパティを定義します。  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. 次のコードを追加することで、クラスのメソッドを定義します。  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. という名前のプロシージャを追加することで、新しいクラスのパラメーター化されたコンス トラクターを定義`Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New`コンス トラクターはこのクラスに基づくオブジェクトが作成されたときに自動的に呼び出されます。 このコンス トラクターは、ユーザー名を保持するフィールドの値を設定します。  
  
## <a name="to-create-a-button-to-test-the-class"></a>クラスをテストするためのボタンを作成するには
  
1. その名前を右クリックしてスタートアップ フォームをデザイン モードに変更**ソリューション エクスプ ローラー**  をクリックし、**ビュー デザイナー**します。 既定では、Windows アプリケーション プロジェクトのスタートアップ フォームは、Form1.vb をという名前です。 メイン フォームが表示されます。  
  
2. メイン フォームにボタンを追加し、ダブルクリックのコードを表示して、`Button1_Click`イベント ハンドラー。 テストのプロシージャを呼び出すには、次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>アプリケーションを実行するには
  
1. F5 キーを押してアプリケーションを実行します。 テストのプロシージャを呼び出すフォーム上のボタンをクリックします。 元のことを示すメッセージを表示`UserName`"MOORE、BOBBY"は、プロシージャが呼び出されるため、`Capitalize`オブジェクトのメソッド。  
  
2. **[OK]** をクリックしてメッセージ ボックスを閉じます。 `Button1 Click`の値を変更する手順、`UserName`プロパティの新しい値のことを示すメッセージを表示および`UserName`"Worden、Joe"は。  
  
## <a name="see-also"></a>関連項目

- [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
