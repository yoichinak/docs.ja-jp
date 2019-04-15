---
title: '方法: XDocument、XElement、または LINQ for XML クエリの結果にバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: afecb87dcfce1a8c48f1b2108edeae3cfd2aa16f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209659"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>方法: XDocument、XElement、または LINQ for XML クエリの結果にバインドする
この例では、XML データの連結、<xref:System.Windows.Controls.ItemsControl>を使用して<xref:System.Xml.Linq.XDocument>します。  
  
## <a name="example"></a>例  
 次の XAML コードを定義、<xref:System.Windows.Controls.ItemsControl>型のデータのデータ テンプレートが含まれています`Planet`で、 `http://planetsNS` XML 名前空間。 名前空間を占有する XML データ型では、名前空間をかっこで囲んで含める必要があります。また、その XML データ型が、XAML マークアップ拡張機能が出現する可能性がある場所に出現する場合は、名前空間の前に、かっこのエスケープ シーケンスを使用して指定する必要があります。 このコードに対応する動的プロパティにバインド、<xref:System.Xml.Linq.XContainer.Element%2A>と<xref:System.Xml.Linq.XElement.Attribute%2A>のメソッド、<xref:System.Xml.Linq.XElement>クラス。 動的プロパティによって、XAML がこれらのメソッドの名前を共有する動的プロパティにバインドできます。 詳細については、「[LINQ to XML の動的プロパティ](/visualstudio/designers/linq-to-xml-dynamic-properties)」を参照してください。 XML 用の既定の名前空間宣言が属性名には適用されないことに注意してください。  
  
 [!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 次の c# のコード呼び出し<xref:System.Xml.Linq.XDocument.Load%2A>という名前の要素のすべてのサブ要素をスタック パネルのデータ コンテキストを設定および`SolarSystemPlanets`で、 `http://planetsNS` XML 名前空間。  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 使用して XAML リソースとして XML データを格納できる<xref:System.Windows.Data.ObjectDataProvider>します。 完全な例を参照してください。 [L2DBForm.xaml ソース コード](/visualstudio/designers/l2dbform-xaml-source-code)します。 次の例は、コードでデータ コンテキストをオブジェクト リソースに設定する方法を示しています。  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 マップされる動的プロパティ<xref:System.Xml.Linq.XContainer.Element%2A>と<xref:System.Xml.Linq.XElement.Attribute%2A>XAML 内の柔軟性を提供します。 コードを LINQ for XML クエリの結果にバインドすることもできます。 この例は、要素の値によって並べられたクエリ結果にバインドします。  
  
 [!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>関連項目

- [バインディング ソースの概要](binding-sources-overview.md)
- [LINQ to XML による WPF のデータ バインディングの概要](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [LINQ to XML を使用した WPF のデータ バインディングの例](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [LINQ to XML の動的プロパティ](/visualstudio/designers/linq-to-xml-dynamic-properties)
