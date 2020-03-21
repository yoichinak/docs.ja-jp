---
title: LINQ to XML の概要
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266899"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic における LINQ to XML の概要
Visual Basic では[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]、XML リテラルおよび XML 軸プロパティをサポートしています。 これにより、Visual Basic コードで XML を操作するための使い慣れた便利な構文を使用できます。 *XML リテラルを*使用すると、コードに XML を直接含めることができます。 *XML 軸プロパティ*を使用すると、子ノード、子孫ノード、および XML リテラルの属性にアクセスできます。 詳細については、「 XML[リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)と[Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)」を参照してください。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]は、統合言語クエリ (LINQ) を利用するために特別に設計されたインメモリ XML プログラミング API です。 LINQ API を直接呼び出すことができますが、XML リテラルを宣言し、XML 軸プロパティに直接アクセスできるのは Visual Basic だけです。  
  
> [!NOTE]
> XML リテラルおよび XML 軸プロパティは、ASP.NET ページの宣言型コードではサポートされていません。 Visual Basic XML 機能を使用するには、ASP.NET アプリケーションの分離コード ページにコードを配置します。  
  
 [再生ボタン](./media/overview-of-linq-to-xml/play-video-icon-example.gif)関連するビデオのデモンストレーションについては、「 [LINQ to XML の使用を開始する方法」](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)および「 LINQ to XML を[使用して Excel スプレッドシートを作成する方法」](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)を参照してください。
  
## <a name="creating-xml"></a>XML の作成  
 XML ツリーを作成する方法は 2 つあります。 XML リテラルは、コードで直接宣言することも、LINQ API を使用してツリーを作成することもできます。 どちらのプロセスも、コードに XML ツリーの最終的な構造を反映させます。 たとえば、次のコード例では、XML 要素を作成します。  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 詳細については、「 [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)」を参照してください。  
  
## <a name="accessing-and-navigating-xml"></a>XML へのアクセスとナビゲーション  
 Visual Basic には、XML 構造にアクセスして移動するための XML 軸プロパティが用意されています。 これらのプロパティを使用すると、XML 子要素名を指定して XML 要素および属性にアクセスできます。 または、要素や属性をナビゲートおよび検索するための LINQ メソッドを明示的に呼び出すことができます。 たとえば、次のコード例では、XML 軸プロパティを使用して、XML 要素の属性と子要素を参照しています。 このコード例では、LINQ クエリを使用して子要素を取得し、XML 要素として出力し、変換を効果的に実行します。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 詳細については、「 [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)」を参照してください。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 Visual Basic では、ステートメントを使用して、グローバル XML 名前空間`Imports`へのエイリアスを指定できます。 次の例は、ステートメントを使用`Imports`して XML 名前空間をインポートする方法を示しています。  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 XML 名前空間エイリアスは、XML 軸プロパティにアクセスし、XML ドキュメントおよび要素の XML リテラルを宣言するときに使用できます。  
  
 [GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)<xref:System.Xml.Linq.XNamespace>演算子を使用して、特定の名前空間プレフィックスのオブジェクトを取得できます。  
  
 詳細については、「[インポート ステートメント (XML 名前空間)」を参照](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)してください。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML リテラルでの XML 名前空間の使用  
 次の例は、グローバル名前空間<xref:System.Xml.Linq.XElement>`ns`を使用するオブジェクトを作成する方法を示しています。  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic コンパイラは、XML 名前空間のエイリアスを含む XML リテラルを`xmlns`、XML 名前空間を使用する XML 表記を使用する等価コードに変換します。 コンパイルすると、前のセクションの例のコードは、次の例と同じ実行可能コードを生成します。  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML 軸プロパティでの XML 名前空間の使用  
 XML リテラルで宣言された XML 名前空間は、XML 軸プロパティでは使用できません。 ただし、グローバル名前空間は、XML 軸プロパティと共に使用できます。 XML 名前空間プレフィックスとローカル要素名を区切るには、コロンを使用します。 たとえば次のようになります。  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [Xml](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
