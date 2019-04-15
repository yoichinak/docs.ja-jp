---
title: イベント ハンドラーの概要 (Windows フォーム)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 05acbfaf427060d015c2445360a7d73ebe97d070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186083"
---
# <a name="event-handlers-overview-windows-forms"></a>イベント ハンドラーの概要 (Windows フォーム)
イベント ハンドラーは、イベントにバインドされるメソッドです イベントが発生したとき、そのイベント ハンドラー内のコードが実行されます 各イベント ハンドラーは、イベントを正しく処理できるように 2 つのパラメーターを提供しています。 次の例では、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを示しています。  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 最初のパラメーター、`sender` はイベントを発生させたオブジェクトへの参照を提供します。  2 番目のパラメーター、 `e`は、上記の例では、処理されたイベントで特有のオブジェクトを渡しています。 そのオブジェクトのプロパティ (また、ときには、そのメソッド) を参照することによって、マウス イベントにおけるマウスの位置や、あるいはドラッグ アンド ドロップのイベントで移動したデータのような情報を取得できます。  
  
 多くのイベントは、2 番目のパラメーターに異なるイベント オブジェクト型を持つ イベント ハンドラーを有しています。 <xref:System.Windows.Forms.Control.MouseDown> や <xref:System.Windows.Forms.Control.MouseUp> のようないくつかのイベント ハンドラーは 2 番目のパラメーターに同じオブジェクト型を持ちます。 この種のイベントでは、両方のイベントを処理するために同じイベント ハンドラーを使用することができます。  
  
 また、異なるコントロールの同じイベントを処理するために同じイベント ハンドラーを使用することもできます。 たとえば、フォーム上に <xref:System.Windows.Forms.RadioButton> のコントロールのグループがある場合、<xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを作成し、それぞれのコントロールの <xref:System.Windows.Forms.Control.Click> イベントをその 1 つのイベント ハンドラーにバインドさせることができます。 詳細については、「[方法 :Windows フォームで 1 つのイベント ハンドラーに複数のイベントを関連付ける](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム内でのイベント ハンドラーの作成](creating-event-handlers-in-windows-forms.md)
- [イベントの概要](events-overview-windows-forms.md)
