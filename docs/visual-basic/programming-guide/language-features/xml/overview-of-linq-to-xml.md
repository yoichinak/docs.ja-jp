---
title: Visual Basic における LINQ to XML の概要
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 91f622b9eecdd1aec8b9361493095e92a851988e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816175"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic における LINQ to XML の概要
Visual Basic のサポートを提供する[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML リテラルおよび XML 軸プロパティを使用します。 これにより、Visual Basic コードで XML を操作するための使い慣れた、便利な構文を使用することができます。 *XML リテラル*コード内で直接 XML を有効にします。 *XML 軸プロパティ*アクセス子ノード、子孫ノード、および XML リテラルの属性を有効にします。 詳細については、[XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)と[Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)を参照してください。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] メモリ内 XML プログラミング API を活用するには、具体的には設計[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]します。 呼び出すことができますが、 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Api を直接、唯一の Visual Basic を使用すると、XML リテラルを宣言し、XML 軸のプロパティに直接アクセスします。  
  
> [!NOTE]
>  ASP.NET ページ内の宣言型コードでは、XML リテラルおよび XML 軸プロパティがサポートされていません。 Visual Basic の XML 機能を使用するには、ASP.NET アプリケーションでの分離コード ページで、コードを配置します。  
  
 ![ビデオへのリンク](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")関連のビデオによるデモを参照してください。 [LINQ to XML による開始するにはどうすればでしょうか。](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)と[LINQ to XML を使用して作成する Excel ワークシートの操作方法?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)します。  
  
## <a name="creating-xml"></a>XML の作成  
 Visual Basic で XML ツリーを作成する 2 つの方法はあります。 コードで直接リテラル XML を宣言することができますか、使用することができます、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ツリーを作成する Api。 両方のプロセスには、XML ツリーの最終構造を反映するようにコードが有効にします。 たとえば、次のコード例は、XML 要素を作成します。  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 詳細については、[Visual Basic における XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)を参照してください。  
  
## <a name="accessing-and-navigating-xml"></a>アクセスして、XML を移動します。  
 Visual Basic にアクセスして XML 構造を移動するための XML 軸プロパティを提供します。 これらのプロパティを使用すると、XML 子要素の名前を指定することによって XML 要素と属性にアクセスできます。 また、明示的に呼び出せる、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]を移動して、要素と属性を検索するためのメソッド。 たとえば、次のコード例は XML 軸のプロパティを使用して、属性と、XML 要素の子要素を参照してください。 コード例では、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]子要素を取得し、それらを効率的に変換を実行する XML 要素として出力をクエリします。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 詳細については、[Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)を参照してください。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 Visual Basic を使用してグローバル XML 名前空間のエイリアスを指定することができます、`Imports`ステートメント。 次の例は、使用する方法を示します、 `Imports` XML 名前空間をインポートするステートメント。  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 XML 軸プロパティにアクセスし、XML ドキュメントおよび要素の XML リテラルを宣言する場合は、XML 名前空間エイリアスを使用できます。  
  
 取得することができます、<xref:System.Xml.Linq.XNamespace>を使用して特定の名前空間プレフィックスのオブジェクト、 [GetXmlNamespace 演算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)します。  
  
 詳細については、[Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)を参照してください。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML リテラルでの XML 名前空間の使用  
 次の例を作成する方法を示しています、<xref:System.Xml.Linq.XElement>グローバル名前空間を使用するオブジェクトを`ns`:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic コンパイラで XML 名前空間を使用するための XML 表記を使用する同等のコードに XML 名前空間エイリアスを含む XML リテラルに変換、`xmlns`属性。 コンパイルされると、前のセクションの例のコードは次の例として本質的に同じ実行可能コードが生成されます。  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML 軸のプロパティでの XML 名前空間の使用  
 XML リテラルで宣言されている XML 名前空間では、XML 軸のプロパティで使用するため使用できません。 ただし、XML 軸のプロパティを持つグローバル名前空間を使用できます。 コロンを使用して、ローカルの要素名から XML 名前空間プレフィックスを区切ります。 例を次に示します。  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
