---
title: '方法: XAML を使用してテーブルを定義する'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 7398af6fddae56238e1af3ee4e726420c01ab7ea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376924"
---
# <a name="how-to-define-a-table-with-xaml"></a>方法: XAML を使用してテーブルを定義する
次の例は、定義する方法を示します、<xref:System.Windows.Documents.Table>を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。  テーブルの例が 4 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>要素) といくつかの行 (によって表される<xref:System.Windows.Documents.TableRow>要素) もデータを格納するいるとタイトル、ヘッダーとフッター情報。  行を含める必要があります、<xref:System.Windows.Documents.TableRowGroup>要素。  テーブル内の各行は 1 つまたは複数のセルで構成されます (によって表される<xref:System.Windows.Documents.TableCell>要素)。  テーブル セル内のコンテンツを含める必要があります、<xref:System.Windows.Documents.Block>要素この例では<xref:System.Windows.Documents.Paragraph>要素が使用されます。  テーブルはハイパーリンクもホスト (によって表される、<xref:System.Windows.Documents.Hyperlink>要素) フッター行にします。  
  
## <a name="example"></a>例  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 この例で定義されたテーブルのレンダリング結果を次の図に示します。  
  
 ![描画されたテーブル。](./media/tableeg.png "TableEG")
