---
title: '方法: LINQ (Visual Basic) を使用した XML を変換します。'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: c34d3988c89e0ce07676e9181200fc039010b50a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324988"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>方法: LINQ (Visual Basic) を使用した XML を変換します。
[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)簡単に 1 つのソースから XML を読み取るし、新しい XML 形式に変換します。 変換、コンテンツを取得する LINQ クエリを利用したり、既存のドキュメントの内容を新しい XML 形式に変更できます。  
  
 このトピックの例では、XML ソース ドキュメントからブラウザーで表示する HTML へのコンテンツを変換します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>XML ドキュメントを変換するには  
  
1. Visual Studio で、新しい Visual Basic プロジェクトを作成、**コンソール アプリケーション**プロジェクト テンプレート。  
  
2. Visual Basic コードを変更するプロジェクトで作成した Module1.vb ファイルをダブルクリックします。 次のコードを追加、`Sub Main`の`Module1`モジュール。 このコードではソース XML ドキュメントとして、<xref:System.Xml.Linq.XDocument>オブジェクト。  
  
    ```vb  
    Dim catalog =   
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
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     [方法: ファイル、文字列、または Stream から XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)。  
  
3. 、元の XML ドキュメントを作成するコードの後に、すべてを取得する次のコードを追加、\<書籍 > オブジェクトの要素を HTML ドキュメントに変換します。 一覧\<Book > 要素のコレクションを返す LINQ クエリを使用して作成<xref:System.Xml.Linq.XElement>変換後の HTML が含まれているオブジェクト。 埋め込み式を使用すると、新しい XML 形式でソース ドキュメントからの値を入力します。  
  
     使用して、結果の HTML ドキュメントがファイルに書き込まれます、<xref:System.Xml.Linq.XElement.Save%2A>メソッド。  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4. 後`Sub Main`の`Module1`、新しいメソッドを追加 (`Sub`) に変換する、\<説明 > ノードが指定された HTML 形式にします。 このメソッドは、前の手順のコードによって呼び出されの形式を保持するために使用、 \<Description > 要素。  
  
     このメソッドのサブ要素が置き換えられます、\<説明 > を持つ HTML 要素。 `ReplaceWith`メソッドは、サブ要素の位置を保持するために使用します。 変換後のコンテンツ、\<説明 > 要素は、HTML の段落に含まれます (\<p >) 要素。 <xref:System.Xml.Linq.XContainer.Nodes%2A>の変換後のコンテンツを取得するプロパティが使用される、 \<Description > 要素。 これにより、変換後のコンテンツにサブ要素が含まれること。  
  
     後は、次のコードを追加`Sub Main`の`Module1`します。  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5. 変更内容を保存します。  
  
6. F5 キーを押して、コードを実行します。 保存されたドキュメントは次のようにします。  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a>関連項目

- [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [方法: ファイル、文字列、またはストリームからの XML の読み込み](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
