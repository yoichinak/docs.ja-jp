---
title: 名前空間の概要 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: 45328fe0ac549086b8abea22c42c7be37fb12b3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665963"
---
# <a name="namespaces-overview-linq-to-xml"></a>名前空間の概要 (LINQ to XML)
このトピックでは、名前空間、<xref:System.Xml.Linq.XName> クラス、および <xref:System.Xml.Linq.XNamespace> クラスについて説明します。  
  
## <a name="xml-names"></a>XML 名  
 XML 名は、多くの場合、XML プログラミングを複雑にしている原因です。 XML 名は、XML 名前空間 (XML 名前空間 URI) とローカル名で構成されます。 XML 名前空間は、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ベースのプログラムにおける名前空間と似ています。 これを使用すると、要素と属性の名前を一意に修飾できます。 このため、XML ドキュメントのさまざまな部分の間で、名前の競合を回避するのに役立ちます。 XML 名前空間を宣言した後は、その名前空間内でのみ一意であるローカル名を選択できます。  
  
 XML 名には、XML *名前空間プレフィックス*という側面もあります。 XML プレフィックスは、XML 名の複雑さの主要な原因です。 このプレフィックスを使用すると、XML 名前空間に対するショートカットを作成できるため、XML ドキュメントがより簡潔でわかりやすくなります。 ただし XML プレフィックスはコンテキストによって意味が異なり、これが複雑さの原因となります。 たとえば、XML プレフィックス `aw` に関連付けられている XML 名前空間が、同じ XML ツリー内でも部分によって異なる可能性があります。  
  
 使用する場合[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic および XML リテラルでは、名前空間内のドキュメントを使用する場合、名前空間プレフィックスを使用する必要があります。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] で XML 名を表すクラスは <xref:System.Xml.Linq.XName> です。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API では XML 名がよく使用されており、XML 名が必要な場合には必ず <xref:System.Xml.Linq.XName> パラメーターが存在します。 しかし、<xref:System.Xml.Linq.XName> を直接操作することはほとんどありません。 <xref:System.Xml.Linq.XName> には、文字列からの暗黙の変換が含まれています。  
  
 詳細については、次のトピックを参照してください。 <xref:System.Xml.Linq.XNamespace> および <xref:System.Xml.Linq.XName>  
  
## <a name="see-also"></a>関連項目

- [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
