---
title: '方法: XAML を使用してテーブルを定義する'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 011f612527f0c9e89ec05643edbb95b2d908488c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776582"
---
# <a name="how-to-define-a-table-with-xaml"></a>方法: XAML を使用してテーブルを定義する
次の例は、定義する方法を示します、<xref:System.Windows.Documents.Table>を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。  テーブルの例が 4 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>要素) といくつかの行 (によって表される<xref:System.Windows.Documents.TableRow>要素) もデータを格納するいるとタイトル、ヘッダーとフッター情報。  行を含める必要があります、<xref:System.Windows.Documents.TableRowGroup>要素。  テーブル内の各行は 1 つまたは複数のセルで構成されます (によって表される<xref:System.Windows.Documents.TableCell>要素)。  テーブル セル内のコンテンツを含める必要があります、<xref:System.Windows.Documents.Block>要素この例では<xref:System.Windows.Documents.Paragraph>要素が使用されます。  テーブルはハイパーリンクもホスト (によって表される、<xref:System.Windows.Documents.Hyperlink>要素) フッター行にします。  
  
## <a name="example"></a>例  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 次の図は、この例で定義されているテーブルの表示方法を示しています。  
  
 ![XAML で定義されたテーブルのスクリーン ショット。](./media/how-to-define-a-table-with-xaml/planetary-information-xaml-table.png)
