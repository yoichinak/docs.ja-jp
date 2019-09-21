---
title: '方法: 進行状況を示す Windows フォーム コントロールを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 84f0caace70f9877e84fdd01dc69216dc10fe485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950571"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>方法: 進行状況を示す Windows フォーム コントロールを作成する
次のコード例は、アプリケーションのレベルまたは進行状況の表示にに使用できる `FlashTrackBar` というカスタム コントロールを示していいます。 これは、グラデーションを使用して、進行状況を視覚的に表示します。  
  
 `FlashTrackBar` コントロールには次のような機能が含まれます。  
  
- カスタム プロパティの定義。  
  
- カスタム イベントの定義 (`FlashTrackBar` が `ValueChanged` イベントを定義します)。  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドをオーバーライドして、コントロールを描画するロジックを提供します。  
  
- <xref:System.Windows.Forms.Control.ClientRectangle%2A>プロパティを使用して、コントロールを描画するために使用できる領域を計算します。 `FlashTrackBar` は、`OptimizedInvalidate` メソッドでこの計算を実行します。  
  
- Windows フォーム デザイナー内でプロパティが変更されたときの、プロパティのシリアル化または永続化の実装。 `FlashTrackBar` は `StartColor` プロパティと `EndColor` プロパティをシリアル化するために、`ShouldSerializeStartColor` メソッドと `ShouldSerializeEndColor` メソッドを定義します。  
  
 `FlashTrackBar` によって定義されるカスタム プロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`AllowUserEdit`|フラッシュ トラック バーをクリックまたはドラッグして値を変更できるかどうかを示します。|  
|`EndColor`|トラック バーの終了色を指定します。|  
|`DarkenBy`|前景のグラデーションを基準にして、背景のグラデーションをどの程度の濃さにするかを指定します。|  
|`Max`|トラック バーの最大値を指定します。|  
|`Min`|トラック バーの最小値を指定します。|  
|`StartColor`|グラデーションの開始色を指定します。|  
|`ShowPercentage`|グラデーションの上にパーセントを表示するかどうかを示します。|  
|`ShowValue`|グラデーションの上に現在の値を表示するかどうかを示します。|  
|`ShowGradient`|現在の値を表示した色のグラデーションをトラック バーに表示するかどうかを示します。|  
|-   `Value`|トラック バーの現在の値を指定します。|  
  
 次の表は、`FlashTrackBar:` によって定義される追加メンバーである、プロパティ変更イベント、およびイベントを発生させるメソッドを示しています。  
  
|メンバー|説明|  
|------------|-----------------|  
|`ValueChanged`|トラック バーの `Value` プロパティが変更されたときに発生するイベント。|  
|`OnValueChanged`|`ValueChanged` イベントを発生させるメソッド。|  
  
> [!NOTE]
> `FlashTrackBar`イベントデータには<xref:System.EventArgs>クラスを、イベントデリゲートにはを<xref:System.EventHandler>使用します。  
  
 対応する*EventName*イベントを処理する`FlashTrackBar`ために、は、から<xref:System.Windows.Forms.Control?displayProperty=nameWithType>継承される次のメソッドをオーバーライドします。  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 対応するプロパティ変更イベントを処理するため`FlashTrackBar`に、は、から<xref:System.Windows.Forms.Control?displayProperty=nameWithType>継承される次のメソッドをオーバーライドします。  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>例  
 `FlashTrackBar` コントロールは、次のコード一覧に示すとおり、`FlashTrackBarValueEditor` と `FlashTrackBarDarkenByEditor` という 2 つの UI 型エディターを定義します。 `HostApp` クラスは、Windows フォームで `FlashTrackBar` コントロールを使用します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>関連項目

- [デザイン時サポートの拡張](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Windows フォーム コントロール開発の基本概念](windows-forms-control-development-basics.md)
