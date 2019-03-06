---
title: '方法: システム フォントを列挙する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352439"
---
# <a name="how-to-enumerate-system-fonts"></a>方法: システム フォントを列挙する
## <a name="example"></a>例  
 次の例では、システム フォントのコレクション内のフォントを列挙する方法を示します。 それぞれのフォント ファミリ名<xref:System.Windows.Media.FontFamily>内<xref:System.Windows.Media.Fonts.SystemFontFamilies%2A>コンボ ボックスに項目として追加されます。  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 同じディレクトリに同じフォント ファミリの複数のバージョンが存在する場合、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]フォントの列挙体は、フォントの最新バージョンを返します。 バージョン情報が解決を提供していない場合は、最新のタイムスタンプを持つフォントが返されます。 タイムスタンプ情報が同等の場合は、アルファベット順で最初のフォント ファイルが返されます。
