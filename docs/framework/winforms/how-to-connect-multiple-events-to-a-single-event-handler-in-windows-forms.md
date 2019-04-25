---
title: '方法: Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: eec6a754b885cd169e5542221caefb3233c4c8af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300724"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>方法: Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける
アプリケーションの設計でする必要がありますを 1 つのイベント ハンドラーを使用して、複数のイベントまたは複数のイベントが、同じ手順を実行します。 たとえば、フォーム上のボタンの場合は、同じ機能を公開するように、同じイベントを発生させるメニュー コマンドを使用して強力な時間を節約では多くの場合です。 [プロパティ] ウィンドウのイベント ビューを使用してこれを行うC#またはを使用して、`Handles`キーワードと**クラス名**と**メソッド名**ドロップダウン ボックスでは、Visual Basic コード エディター。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Visual Basic での 1 つのイベント ハンドラーに複数のイベントを接続するには  
  
1. フォームを右クリックし **コードの表示**します。  
  
2. **クラス名**ドロップダウン ボックスで、イベント ハンドラーが処理するコントロールのいずれかを選択します。  
  
3. **メソッド名**ドロップダウン ボックスで、イベント ハンドラーが処理するイベントは、のいずれかを選択します。  
  
4. コード エディターでは、適切なイベント ハンドラーを挿入し、メソッド内でカーソルを配置します。 次の例では、<xref:System.Windows.Forms.Control.Click>イベントを<xref:System.Windows.Forms.Button>コントロール。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. 他のイベントを処理を追加、`Handles`句。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. イベント ハンドラーに、適切なコードを追加します。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>C での 1 つのイベント ハンドラーに複数のイベントを接続するには\#
  
1. イベント ハンドラーを接続するコントロールを選択します。  
  
2. [プロパティ] ウィンドウ、**イベント**ボタン (![イベント ボタン](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。  
  
3. 処理するイベントの名前をクリックします。  
  
4. イベント名の横の [値] セクションでは、処理するイベントのメソッド シグネチャに一致する既存のイベント ハンドラーの一覧を表示するドロップダウン ボタンをクリックします。  
  
5. 一覧から適切なイベント ハンドラーを選択します。  
  
     コードは、既存のイベント ハンドラーにイベントをバインドするフォームに追加されます。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム内でのイベント ハンドラーの作成](creating-event-handlers-in-windows-forms.md)
- [イベント ハンドラーの概要](event-handlers-overview-windows-forms.md)
