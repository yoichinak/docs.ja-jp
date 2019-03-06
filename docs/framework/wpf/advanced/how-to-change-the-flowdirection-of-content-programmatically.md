---
title: '方法: プログラムによってコンテンツの FlowDirection を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: ec159ed0efce8b5514788331e8715a55e7a8a638
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359329"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>方法: プログラムによってコンテンツの FlowDirection を変更する
この例は、プログラムで変更する方法を示します、<xref:System.Windows.FrameworkElement.FlowDirection%2A>のプロパティを<xref:System.Windows.Controls.FlowDocumentReader>します。  
  
## <a name="example"></a>例  
 2 つ<xref:System.Windows.Controls.Button>要素が作成可能な値のいずれかを表す各<xref:System.Windows.FlowDirection>します。 内容に関連付けられているプロパティ値を適用するボタンがクリックされたときに、<xref:System.Windows.Controls.FlowDocumentReader>という`tf1`します。  プロパティの値に書き込まれます、<xref:System.Windows.Controls.TextBlock>という`txt1`します。  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>例  
 上記で定義されたボタンのクリックに関連付けられているイベントで処理をC#分離コード ファイル。  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
