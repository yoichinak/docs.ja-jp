---
title: '方法: メッセージ ボックスを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: fa371b62c78a08e25de815fa44360230b6156008
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369605"
---
# <a name="how-to-open-a-message-box"></a>方法: メッセージ ボックスを開く
この例では、メッセージ ボックスを開く方法を示します。  
  
## <a name="example"></a>例  
 メッセージ ボックスは、ユーザーに情報を表示する作成済みのモーダル ダイアログ ボックスです。 静的なを呼び出すことによって、メッセージ ボックスが開かれる<xref:System.Windows.MessageBox.Show%2A>のメソッド、<xref:System.Windows.MessageBox>クラス。 ときに<xref:System.Windows.MessageBox.Show%2A>が呼び出されると、メッセージが渡される文字列パラメーターを使用します。 複数のオーバー ロード<xref:System.Windows.MessageBox.Show%2A>メッセージ ボックスの表示方法を構成することを許可する (を参照してください<xref:System.Windows.MessageBox>)。  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>関連項目
- [メッセージ ボックスのサンプル](https://go.microsoft.com/fwlink/?LinkID=160023)
