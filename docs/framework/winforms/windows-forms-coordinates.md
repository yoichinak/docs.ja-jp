---
title: Windows フォームの座標
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: 6feabadff17538f4a7368c348f7b72226e2d678e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800153"
---
# <a name="windows-forms-coordinates"></a>Windows フォームの座標
Windows フォームの座標システムは、デバイス座標に基づいており、Windows フォームで描画するときに、メジャーの基本単位はデバイス単位 (通常は、ピクセル) です。 画面上の点は、増加、右、上から下に増やすと、y 座標の x 座標と、x 座標と y 座標のペアで説明します。 画面を基準とした、元の場所は、画面またはクライアント座標を指定するかどうかによって異なります。  
  
## <a name="screen-coordinates"></a>画面座標  
 Windows フォーム アプリケーションでは、画面座標では、画面上のウィンドウの位置を指定します。 画面座標の原点は、画面の左上隅です。 ウィンドウの完全な位置がによって定義された多くの場合、<xref:System.Drawing.Rectangle>ウィンドウの左上隅および右の角を定義する 2 つの点の画面座標を含む構造体。  
  
## <a name="client-coordinates"></a>クライアント座標  
 Windows フォーム アプリケーションでは、フォームまたはコントロールのクライアント座標を使用してポイントの位置を指定します。 クライアント座標の原点は、コントロールまたはフォームのクライアント領域の左上隅です。 クライアント座標では、アプリケーションがフォームまたはフォームまたは画面上のコントロールの位置に関係なく、コントロールの描画中に一貫性のある座標値を使用することを確認します。  
  
 クライアント領域のディメンションがによって記述も、<xref:System.Drawing.Rectangle>領域のクライアント座標を含む構造体。 どの場合も、右下の座標が除外されているときに、クライアント領域に四角形の左上隅の座標が含まれます。 グラフィックスの操作は、クライアント領域の右および下端を含めないでください。 たとえば、<xref:System.Drawing.Graphics.FillRectangle%2A>メソッドは、指定した四角形の右方向と下の端にいっぱいになりますが、これらのエッジは含まれません。  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>座標の 1 つの型から別のマッピング  
 場合によっては、画面座標からクライアント座標にマップする必要があります。 簡単にこれを使用して、<xref:System.Windows.Forms.Control.PointToClient%2A>と<xref:System.Windows.Forms.Control.PointToScreen%2A>メソッドで使用できる、<xref:System.Windows.Forms.Control>クラス。 たとえば、<xref:System.Windows.Forms.Control.MousePosition%2A>プロパティの<xref:System.Windows.Forms.Control>画面座標で報告されたクライアント座標に変換することができます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
