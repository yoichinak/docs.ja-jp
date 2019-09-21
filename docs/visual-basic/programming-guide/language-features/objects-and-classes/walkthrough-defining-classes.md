---
title: クラスの定義 (Visual Basic)
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
ms.openlocfilehash: 679f4fd55f142c2c4bb63a556feb95c074960b12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914730"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>チュートリアル: クラスの定義 (Visual Basic)

このチュートリアルでは、クラスを定義する方法を示します。このクラスを使用してオブジェクトを作成できます。 また、新しいクラスにプロパティとメソッドを追加する方法と、オブジェクトを初期化する方法についても説明します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>クラスを定義するには
  
1. **[ファイル]** メニューの **[新しいプロジェクト]** をクリックして、プロジェクトを作成します。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2. Visual Basic プロジェクトテンプレートの一覧から [Windows アプリケーション] を選択して、新しいプロジェクトを表示します。  
  
3. **[プロジェクト]** メニューの **[クラスの追加]** をクリックして、新しいクラスをプロジェクトに追加します。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
4. **クラス**テンプレートを選択します。  
  
5. 新しい`UserNameInfo.vb`クラスにという名前を指定し、 **[追加]** をクリックして新しいクラスのコードを表示します。  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > Visual Basic**コードエディター**を使用して、クラスをスタートアップフォームに追加するには、 `Class`キーワードに続けて新しいクラスの名前を入力します。 **コードエディター**には、対応`End Class`するステートメントが用意されています。  
  
6. ステートメントと`Class` `End Class`ステートメントの間に次のコードを追加して、クラスのプライベートフィールドを定義します。  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     フィールドをとし`Private`て宣言することは、クラス内でのみ使用できることを意味します。 など`Public`のアクセス修飾子を使用して、クラスの外部からフィールドを使用できるようにすることができます。これにより、より多くのアクセス権が提供されます。 詳細については、[ Visual Basic のアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
7. 次のコードを追加して、クラスのプロパティを定義します。  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. 次のコードを追加して、クラスのメソッドを定義します。  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. という名前`Sub New`のプロシージャを追加して、新しいクラスのパラメーター化されたコンストラクターを定義します。  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     コンストラクター `Sub New`は、このクラスに基づくオブジェクトが作成されるときに自動的に呼び出されます。 このコンストラクターは、ユーザー名を保持するフィールドの値を設定します。  
  
## <a name="to-create-a-button-to-test-the-class"></a>クラスをテストするボタンを作成するには
  
1. **ソリューションエクスプローラー**で名前を右クリックし、 **[デザイナーの表示]** をクリックして、スタートアップフォームをデザインモードに変更します。 既定では、Windows アプリケーションプロジェクトのスタートアップフォームには、Form1.vb という名前が付けられています。 メインフォームが表示されます。  
  
2. メインフォームにボタンを追加し、それをダブルクリックして`Button1_Click`イベントハンドラーのコードを表示します。 次のコードを追加して、テストプロシージャを呼び出します。  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>アプリケーションを実行するには
  
1. F5 キーを押してアプリケーションを実行します。 フォーム上のボタンをクリックして、テストプロシージャを呼び出します。 このメソッドは、オブジェクトのメソッドを`UserName` `Capitalize`呼び出したため、元のが "真人, 村中" であることを示すメッセージを表示します。  
  
2. **[OK]** をクリックしてメッセージ ボックスを閉じます。 この`Button1 Click`プロシージャは`UserName`プロパティの値を変更し、の`UserName`新しい値が "?" であることを示すメッセージを表示します。  
  
## <a name="see-also"></a>関連項目

- [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
