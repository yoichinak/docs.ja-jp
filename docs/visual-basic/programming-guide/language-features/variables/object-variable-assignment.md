---
title: オブジェクト変数への代入 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: dff1b9bb9e87f827663786cac3f33531db41b2c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840277"
---
# <a name="object-variable-assignment-visual-basic"></a>オブジェクト変数への代入 (Visual Basic)
オブジェクトをオブジェクト変数に代入するのにには、通常代入ステートメントを使用します。 オブジェクト式を割り当てることができます、または[Nothing](../../../../visual-basic/language-reference/nothing.md)キーワードでは、次の例として示します。  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` 変数に現在割り当てられているオブジェクトが存在しないことを意味します。  
  
## <a name="initialization"></a>初期化  
 コードが実行されている変数に初期化されるオブジェクトが開始すると`Nothing`します。 宣言には初期化が含まれているが、宣言ステートメントの実行時に指定する値を再初期化されます。  
  
 使用して、宣言で初期化を含めることができます、[新規](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード。 次の宣言ステートメントは、オブジェクト変数を宣言`testUri`と`ver`し、特定のオブジェクトを割り当てます。 それぞれは、オブジェクトを初期化するために、適切なクラスのオーバー ロードされたコンス トラクターのいずれかを使用します。  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>関連付けの解除  
 オブジェクト変数を設定`Nothing`と特定のオブジェクト変数の関連付けは失われます。 こうと、誤って、変数を変更することで、オブジェクトを変更します。 オブジェクト変数は、次の例として有効なオブジェクトをポイントするかどうかをテストすることもできます。  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 変数が参照するオブジェクトが別のアプリケーションの場合は、このテストはそのアプリケーションが終了またはだけオブジェクトを無効にするかどうかを判断できません。  
  
 オブジェクト変数の値を持つ`Nothing`ともいいます、 *null 参照*します。  
  
## <a name="current-instance"></a>現在のインスタンス  
 *現在インスタンス*オブジェクトが現在のコードが実行されている 1 つ。 プロシージャ内にある、すべてのコードの実行後、現在のインスタンスは、プロシージャが呼び出された 1 つが。  
  
 `Me`キーワードは、現在のインスタンスを参照するオブジェクト変数として機能します。 プロシージャがない場合[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)、使用できる、`Me`キーワードを現在のインスタンスへのポインターを取得します。 共有プロシージャは、クラスの特定のインスタンスに関連付けすることはできません。  
  
 使用して`Me`は現在のインスタンスを別のモジュール内のプロシージャに渡すために特に便利です。 たとえば、さまざまな XML ドキュメントがあり、それらすべてにいくつかの標準のテキストを追加することです。 次の例では、これを実行するプロシージャを定義します。  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 すべての XML ドキュメント オブジェクトでしたし、プロシージャを呼び出すし、現在のインスタンスを引数として渡します。 次に例を示します。  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [方法: オブジェクト変数を宣言し、Visual Basic でオブジェクトを割り当てる](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [方法: オブジェクトが変数になる任意のインスタンスを参照していません](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
