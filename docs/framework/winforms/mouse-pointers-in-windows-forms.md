---
title: Windows フォームにおけるマウス ポインター
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: c018986498bfbd7e492c3e7a26c94e0baa0576d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712735"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows フォームにおけるマウス ポインター
マウス*ポインター*、ユーザー入力、マウスで画面のフォーカス ポイントを指定するビットマップには、そのカーソルと呼ばします。 このトピックでは、Windows フォームにおけるマウス ポインターの概要を示し、いくつかの変更およびマウス ポインターを制御する方法について説明します。  
  
## <a name="accessing-the-mouse-pointer"></a>マウスのポインターへのアクセス  
 マウス ポインターがによって表される、<xref:System.Windows.Forms.Cursor>クラス、および各<xref:System.Windows.Forms.Control>が、<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>そのコントロールのポインターを指定するプロパティ。 <xref:System.Windows.Forms.Cursor>クラスにはなど、ポインターを記述するプロパティが含まれています、<xref:System.Windows.Forms.Cursor.Position%2A>と<xref:System.Windows.Forms.Cursor.HotSpot%2A>プロパティ、およびメソッドなど、ポインターの外観を変更できる、 <xref:System.Windows.Forms.Cursor.Show%2A>、 <xref:System.Windows.Forms.Cursor.Hide%2A>、および<xref:System.Windows.Forms.Cursor.DrawStretched%2A>メソッド。  
  
## <a name="controlling-the-mouse-pointer"></a>マウス ポインターを制御します。  
 場合によって、マウス ポインターが使用できるまたはマウスの位置を変更する領域を制限したい場合があります。 取得またはを使用して、マウスの現在の場所を設定することができます、<xref:System.Windows.Forms.Cursor.Position%2A>のプロパティ、<xref:System.Windows.Forms.Cursor>します。 マウス ポインターを使用する領域を制限するさらに、設定、<xref:System.Windows.Forms.Cursor.Clip%2A>プロパティ。 クリップ領域で、既定では、全体の画面です。  
  
## <a name="changing-the-mouse-pointer"></a>マウス ポインターを変更します。  
 マウス ポインターを変更すると、ユーザーにフィードバックを提供するための重要な点です。 ハンドラーでマウス ポインターを変更するなど、<xref:System.Windows.Forms.Control.MouseEnter>と<xref:System.Windows.Forms.Control.MouseLeave>イベント計算が行われていることをユーザーに指示して、コントロール内のユーザーの操作を制限します。 場合によっては、マウス ポインターが、アプリケーションがドラッグ アンド ドロップ操作に関係している場合など、システム イベントによって変更されます。  
  
 マウス ポインターを変更する主な方法は、設定して、<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.Control.DefaultCursor%2A>を新しいコントロールのプロパティの<xref:System.Windows.Forms.Cursor>します。 マウス ポインターを変更する例のコード例を参照してください、<xref:System.Windows.Forms.Cursor>クラス。 さらに、<xref:System.Windows.Forms.Cursors>クラスのセットを公開する<xref:System.Windows.Forms.Cursor>ポインター、手の形のようなポインターなどのさまざまな種類のオブジェクト。 砂時計コントロールにマウス ポインターがあるたびに似ていますが、待機のポインターを表示するには使用、<xref:System.Windows.Forms.Control.UseWaitCursor%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラス。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Cursor>
- [Windows フォーム アプリケーションにおけるマウス入力](mouse-input-in-a-windows-forms-application.md)
- [Windows フォームにおけるドラッグ アンド ドロップ機能](drag-and-drop-functionality-in-windows-forms.md)
