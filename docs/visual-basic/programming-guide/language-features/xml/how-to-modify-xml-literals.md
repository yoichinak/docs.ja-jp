---
title: '方法: XML リテラル (Visual Basic) の変更します。'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 003715b04f3a5c0fb41e846beb189f117378ea58
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675330"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>方法: XML リテラル (Visual Basic) の変更します。

Visual Basic では、XML リテラルを変更する便利な手段を提供します。 追加したり、要素と属性を削除し、新しい XML 要素を持つ既存の要素を置換することもできます。 このトピックでは、既存の XML リテラルを変更する方法のいくつかの例を示します。

### <a name="to-modify-the-value-of-an-xml-literal"></a>XML リテラルの値を変更するには

1. XML リテラルの値を変更するには、XML リテラルおよび設定への参照を取得、`Value`プロパティを目的の値にします。

    次のコード例は、すべての値を更新、\<価格 > XML ドキュメント内の要素。

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    次は、サンプルのソース XML に示し、このコード例から XML に変更されました。

    ソース XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    変更された XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > `Value`プロパティはコレクション内の最初の XML 要素を参照します。 コレクションで同じ名前を持つ 1 つ以上の要素がある場合は、設定、`Value`プロパティがコレクション内の最初の要素だけに影響します。

### <a name="to-add-an-attribute-to-an-xml-literal"></a>XML リテラルに属性を追加するには

1. XML リテラルには、属性を追加するには、リテラルの XML への参照をまず取得します。 新しい XML 属性軸プロパティを追加することで、属性を追加できます。 追加することも、新しい<xref:System.Xml.Linq.XAttribute>オブジェクトを XML リテラルを使用して、<xref:System.Xml.Linq.XContainer.Add%2A>メソッド。 次の例では、両方のオプションを示します。

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    次は、サンプルのソース XML に示し、このコード例から XML に変更されました。

    ソース XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    変更された XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    XML 属性軸プロパティの詳細については、[XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)を参照してください。

### <a name="to-add-an-element-to-an-xml-literal"></a>XML リテラルに要素を追加するには

1. XML リテラルには、要素を追加するには、リテラルの XML への参照をまず取得します。 追加できる新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して要素の最後のサブ要素として、<xref:System.Xml.Linq.XContainer.Add%2A>メソッド。 新しいを追加する<xref:System.Xml.Linq.XElement>オブジェクトを使用して最初のサブ要素として、<xref:System.Xml.Linq.XContainer.AddFirst%2A>メソッド。

    その他のサブ要素を基準に特定の場所に新しい要素を追加するには、隣接するサブ要素への参照をまず取得します。 追加できる新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して隣接するサブ要素の前に、<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>メソッド。 追加することも、新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して隣接するサブ要素の後に、<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>メソッド。

    次の例では、これらの各手法の例を示します。

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    次は、サンプルのソース XML に示し、このコード例から XML に変更されました。

    ソース XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    変更された XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>XML リテラルから要素または属性を削除するには

1. XML リテラルから要素または属性を削除するには、要素または属性と呼び出しへの参照を取得、`Remove`メソッドを次の例に示すようにします。

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    次は、サンプルのソース XML に示し、このコード例から XML に変更されました。

    ソース XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    変更された XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    XML リテラルからすべての要素または属性を削除するに XML リテラルへの参照を取得し、呼び出し、<xref:System.Xml.Linq.XElement.RemoveAll%2A>メソッド。

### <a name="to-modify-an-xml-literal"></a>XML リテラルを変更するには

1. XML 要素の名前を変更するには、要素への参照をまず取得します。 新しいを作成できます<xref:System.Xml.Linq.XElement>オブジェクトを持つ新しい名前を指定し、新しい渡す<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XNode.ReplaceWith%2A>メソッドは、既存の<xref:System.Xml.Linq.XElement>オブジェクト。

    自分が置き換える要素のサブ要素を保持する必要がありますが、新しい値を設定<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XContainer.Nodes%2A>は既存の要素のプロパティ。 これにより、既存の要素の内部 XML を新しい要素の値が設定されます。 それ以外の場合に新しい要素の値を設定することができます、`Value`は既存の要素のプロパティ。

    次のコード例は、すべてが置き換わります\<説明 > を持つ要素を\<抽象 > 要素。 コンテンツ、\<説明 > 要素は、新しい保持\<抽象 > 要素を使用して、<xref:System.Xml.Linq.XContainer.Nodes%2A>のプロパティ、\<説明 ><xref:System.Xml.Linq.XElement>オブジェクト。

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    次は、サンプルのソース XML に示し、このコード例から XML に変更されました。

    ソース XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    変更された XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a>関連項目

- [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [方法: ファイル、文字列、または Stream から XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
