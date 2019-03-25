---
title: RaiseEvent ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: ffe08dc8aeef9498d2e9f4c973c5ccbc31fec0b9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973302"
---
# <a name="raiseevent-statement"></a>RaiseEvent ステートメント
クラス、フォーム、またはドキュメント内のモジュール レベルで宣言されているイベントをトリガーします。  
  
## <a name="syntax"></a>構文  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>指定項目  
 `eventname`  
 必須。 トリガーするイベントの名前。  
  
 `argumentlist`  
 任意。 変数、配列、または式のコンマ区切りのリスト。 `argumentlist`引数はかっこで囲む必要があります。 引数がない場合は、かっこを省略する必要があります。  
  
## <a name="remarks"></a>Remarks  
 必要な`eventname`は、モジュール内で宣言されたイベントの名前。 Visual Basic 変数の名前付け規則に従います。  
  
 イベントが発生したモジュール内で宣言されていない、エラーが発生します。 次のコード フラグメントは、イベントの宣言とイベントが発生したプロシージャを示しています。  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 使用することはできません`RaiseEvent`モジュールで明示的に宣言されていないイベントを発生させます。 たとえば、すべてのフォームの継承、<xref:System.Windows.Forms.Control.Click>からイベント<xref:System.Windows.Forms.Form?displayProperty=nameWithType>を使用して、発生することはできません`RaiseEvent`派生フォームでします。 宣言する場合、`Click`イベント モジュールでは、フォーム、フォーム自体のシャドウ<xref:System.Windows.Forms.Control.Click>イベント。 フォームを呼び出すことができますも<xref:System.Windows.Forms.Control.Click>イベントを呼び出すことによって、<xref:System.Windows.Forms.Control.OnClick%2A>メソッド。  
  
 既定では、Visual Basic で定義されたイベントは、接続が確立されている順序では、そのイベント ハンドラーを生成します。 イベントがあるため`ByRef`パラメーター、接続するプロセスは以前のイベント ハンドラーによって変更されているパラメーターを受け取ることがあります。 イベント ハンドラーの実行後は、イベントを発生させたサブルーチンに制御が返されます。  
  
> [!NOTE]
>  非共有イベントは、宣言されているクラスのコンス トラクター内では発生しません。 このようなイベントでは、実行時エラーが発生しない、関連付けられているイベント ハンドラーによってキャッチするされない場合があります。 使用して、`Shared`修飾子をコンス トラクターからイベントを発生させる必要がある場合は、共有イベントを作成します。  
  
> [!NOTE]
>  イベントの既定の動作を変更するには、カスタム イベントを定義します。 カスタム イベントの場合、`RaiseEvent`ステートメントで呼び出されるイベントの`RaiseEvent`アクセサー。 カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。  
  
## <a name="example"></a>例  
 次の例では、イベントを使用して 10 秒から 0 秒までカウント ダウンします。 このコードはいくつかのイベントに関連するメソッド、プロパティ、およびなど、ステートメント、`RaiseEvent`ステートメント。  
  
 イベントを発生させるクラスをイベント ソース、イベントを処理するメソッドをイベント ハンドラーと呼びます。 イベント ソースでは、生成されるイベントに対して複数のイベント ハンドラーを設定できます。 クラスでイベントが発生すると、そのイベントは、オブジェクトのインスタンスに対するイベントを処理するために選択されたすべてのクラスで発生します。  
  
 また、この例では、ボタン (`Button1`) とテキスト ボックス (`TextBox1`) を含んだフォーム (`Form1`) も使用しています。 ボタンをクリックすると、1 つ目のテキスト ボックスに 10 秒から 0 秒までのカウントダウンが表示されます。 カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
 `Form1` のコードでは、フォームの初期状態と終了状態を指定しています。 イベント発生時に実行されるコードも含まれています。  
  
 この例を使用する新しい Windows アプリケーション プロジェクトを開き、という名前のボタンを追加`Button1`という名前のテキスト ボックスと`TextBox1`という名前のメイン フォームに`Form1`します。 次にフォームを右クリックし、をクリックして**コードの表示**コード エディターを開きます。  
  
 追加、`WithEvents`変数の宣言セクションに、`Form1`クラス。  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>例  
 `Form1` のコードに次のコードを追加します。 など、存在するすべての重複するプロシージャを置き換える`Form_Load`、または`Button_Click`します。  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 前の例を実行し、ボタンをクリックします。 f5 キーを押して**開始**します。 最初のテキスト ボックスで、秒のカウント ダウンが開始されます。 カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
> [!NOTE]
>  `My.Application.DoEvents`フォームは、メソッドがまったく同じ方法でイベントを処理できません。 使用することができます、イベントを直接処理するためのフォームは、マルチ スレッドです。 詳細については、次を参照してください。[マネージ スレッド処理](../../../standard/threading/index.md)します。  
  
## <a name="see-also"></a>関連項目
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
