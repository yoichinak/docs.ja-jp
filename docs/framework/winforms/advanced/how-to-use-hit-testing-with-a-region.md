---
title: '方法: ヒット テストをリージョンと使用'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: a9435724e7674fd196ad70bdfd0ab43808a53058
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709746"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>方法: ヒット テストをリージョンと使用
ヒット テストの目的では、アイコンやボタンなどの特定のオブジェクトの上にカーソルがかどうかを決定します。  
  
## <a name="example"></a>例  
 次の例では、2 つの四角形領域の和集合を形成して十字型の領域を作成します。 ある変数`point`最新のクリックの位置を保持します。 コードを調べますかどうか`point`十字型の領域にします。 ポイントは、リージョン (ヒット) では場合、は、非透過の赤いブラシで領域が入力されます。 それ以外の場合、領域は、半透明の赤いブラシで塗りつぶされます。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Region>
- [GDI+ での領域](regions-in-gdi.md)
- [方法: クリッピング領域を使用します。](how-to-use-clipping-with-a-region.md)
