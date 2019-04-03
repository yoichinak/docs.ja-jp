---
title: Property プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828350"
---
# <a name="property-procedures-visual-basic"></a>Property プロシージャ (Visual Basic)
プロパティ プロシージャは、一連のモジュール、クラスまたは構造体のカスタム プロパティを操作する Visual Basic ステートメントです。 プロパティ プロシージャとも呼ばれます*プロパティ アクセサー*します。  
  
 Visual Basic は、次のプロパティ プロシージャを提供します。  
  
-   A`Get`プロパティの値を返します。 式でプロパティにアクセスするときに呼び出されます。  
  
-   A`Set`プロシージャに値をオブジェクト参照を含むプロパティを設定します。 プロパティに値を割り当てるときに呼び出されます。  
  
 使用して、ペアで、通常、プロパティ プロシージャを定義する、`Get`と`Set`プロパティが読み取り専用の場合は、ステートメントがからだけでいずれかの手順に定義することができます ([Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)) または書き込み専用 ([設定ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md))。  
  
 省略することができます、`Get`と`Set`プロシージャの自動実装プロパティを使用する場合。 詳細については、「[自動実装プロパティ](./auto-implemented-properties.md)」を参照してください。  
  
 プロパティは、クラス、構造、およびモジュールで定義できます。 プロパティは、`Public`どこからでも呼び出すことを意味する既定では、プロパティのコンテナーにアクセスできるアプリケーションでします。  
  
 プロパティと変数の比較は、次を参照してください。[プロパティ間の相違点と Visual Basic における変数](./differences-between-properties-and-variables.md)します。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 プロパティ自体がで囲まれたコードのブロックで定義されている、 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメント。 このブロック内で各プロパティ プロシージャは、宣言ステートメントで囲まれた内部ブロックとして表示されます。 (`Get`または`Set`) と一致する`End`宣言します。  
  
 プロパティと、プロシージャの宣言の構文は次のとおりです。  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers`を指定できますアクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウ、に関する情報も、プロパティが読み取り専用または書き込み専用のかどうか。 `AccessLevel`上、`Get`または`Set`プロシージャには、プロパティ自体に指定されたアクセス レベルより限定的な任意のレベルがあります。 詳細については、次を参照してください。 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)します。  
  
### <a name="data-type"></a>データの種類  
 プロパティのデータ型とプリンシパルのアクセス レベルで定義されます、`Property`プロパティ プロシージャではなく、ステートメント。 プロパティは、1 つのデータ型を持つことができます。 たとえば、格納するプロパティを定義することはできません、`Decimal`値しますが、取得、`Double`値。  
  
### <a name="access-level"></a>アクセス レベル  
 ただし、プロパティのプリンシパルのアクセス レベルを定義し、さらに、プロパティ プロシージャのいずれかでアクセス レベルを制限できます。 たとえば、定義することができます、`Public`プロパティを定義し、`Private Set`プロシージャ。 `Get`プロシージャまま`Public`します。 行うことができますのみがプリンシパルのアクセス レベルよりもより制限の厳しいと、プロパティの手順の 1 つだけに、アクセス レベルを変更できます。 詳細については、「[方法 :混合アクセス レベルでプロパティを宣言](./how-to-declare-a-property-with-mixed-access-levels.md)します。  
  
## <a name="parameter-declaration"></a>パラメーターの宣言  
 各パラメーターのと同じ方法を宣言する[Sub プロシージャ](./sub-procedures.md)引き渡し方法がありますが、`ByVal`します。  
  
 パラメーター リスト内の各パラメーターの構文は次のとおりです。  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 パラメーターが省略可能な場合は、その宣言の一部として既定値も指定する必要があります。 既定値を指定する構文は次のとおりです。  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>プロパティ値  
 `Get`プロシージャ、戻り値は、プロパティの値として呼び出し元の式に渡されます。  
  
 `Set`プロシージャのパラメーターに新しいプロパティ値が渡される、`Set`ステートメント。 パラメーターを明示的に宣言する場合は、プロパティと同じデータ型で宣言する必要があります。 コンパイラは、暗黙のパラメーターを使用するパラメーターを宣言していない場合`Value`をプロパティに割り当てられる新しい値を表します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 プロパティ プロシージャは、プロパティを参照することによって暗黙的を呼び出します。 使用するプロパティの名前、変数の名前を使用する場合と同じ方法は、省略できないすべての引数の値を指定する必要がありますが、引数リストをかっこで囲む必要があります。 引数が指定されていない場合、かっこを省略することができます。  
  
 暗黙的な呼び出しの構文、`Set`手順のとおりです。  
  
 `propertyname[(argumentlist)] = expression`  
  
 暗黙的な呼び出しの構文、`Get`手順のとおりです。  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次のプロパティは、2 つの構成名、名、および、最後の名前として、完全な名前を格納します。 呼び出し元のコードを読み取るとき`fullName`、`Get`プロシージャは、2 つの構成名を結合し、完全な名前を返します。 呼び出し元のコードによって、新しい完全な名前を割り当てられるとき、`Set`プロシージャは、それを 2 つの部分に分割しようと試みます。 場所が見つからない場合すべて最初の名前として格納します。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 次の例では、一般的なプロパティ プロシージャの呼び出し`fullName`します。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Function プロシージャ](./function-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: プロパティを作成します。](./how-to-create-a-property.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)
- [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md)
