---
title: プロシージャのオーバーロード (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 14a31c440861cdc2296bcd02357e5fe0004bf359
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638856"
---
# <a name="procedure-overloading-visual-basic"></a>プロシージャのオーバーロード (Visual Basic)
*オーバー ロード*プロシージャでは、異なるパラメーター リストが同じ名前を使用して、複数のバージョンを定義することを意味します。 オーバー ロードの目的では、名前で区別せずに密接に関連するいくつかのバージョンのプロシージャを定義します。 パラメーター リストをさまざまなこれを行います。  
  
## <a name="overloading-rules"></a>オーバー ロードの規則  
 プロシージャをオーバー ロードする場合は、次の規則が適用されます。  
  
- **同じ名前**します。 各オーバー ロードされたバージョンでは、同じプロシージャ名を使用する必要があります。  
  
- **異なる署名**します。 各オーバー ロードされたバージョンは、次のうちの少なくとも 1 つにその他のすべてのオーバー ロードされたバージョンと異なる必要があります。  
  
    - パラメーターの数  
  
    - パラメーターの順序  
  
    - パラメーターのデータ型  
  
    - (ジェネリック プロシージャの場合) の型パラメーターの数  
  
    - 戻り値の型 (変換演算子) の場合のみ  
  
     プロシージャ名、と共に、上記の項目は、総称、*署名*プロシージャのです。 オーバー ロードされたプロシージャを呼び出すときに、コンパイラは、呼び出しが、定義を正しくと一致することを確認するのに署名を使用します。  
  
- **シグネチャの一部ではない項目**します。 シグネチャを変更せず、プロシージャをオーバー ロードすることはできません。 具体的には、プロシージャをオーバー ロードするだけで、次のものの 1 つ以上ことはできません。  
  
    - プロシージャ修飾子キーワードなど`Public`、`Shared`と `Static`  
  
    - パラメーターまたは型パラメーター名  
  
    - (ジェネリック プロシージャの場合) の型パラメーターの制約  
  
    - パラメーター修飾子キーワードなど`ByRef`と `Optional`  
  
    - 値を返すかどうか  
  
    - (変換演算子) を除く、戻り値のデータ型  
  
     上記のリスト項目は、シグネチャの一部ではありません。 オーバー ロードされたバージョンを区別するために、それらを使用することはできませんは、そのシグネチャで区別する、オーバー ロードされたバージョン間で異なることができます。  
  
- **遅延バインディング引数**します。 として適切なパラメーターを宣言する必要があります、オーバー ロードされたバージョンに遅延バインディング オブジェクト変数を渡す場合は、<xref:System.Object>します。  
  
## <a name="multiple-versions-of-a-procedure"></a>プロシージャの複数のバージョン  
 作成すると、`Sub`に対して顧客のバランスでは、トランザクションをポストするプロシージャが名またはアカウントの数のいずれかを顧客に参照することができるようにします。 これに合わせて、2 つの異なる定義できます`Sub`手順については、次の例のように。  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a>オーバー ロードされたバージョン  
 別の方法では、1 つのプロシージャ名をオーバー ロードします。 使用することができます、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワードを次のように各パラメーター一覧については、プロシージャのバージョンを定義します。  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a>追加のオーバー ロード  
 いずれかでトランザクションの量をそのまま使用したい場合`Decimal`または`Single`、オーバー ロードすることがさらに`post`このバリエーションの 1 つを許可します。 これを実行した場合に上記の例ではオーバー ロードごとに、4 つ必要がある`Sub`4 つの異なるシグネチャを持つが、同じ名前のすべての手順。  
  
## <a name="advantages-of-overloading"></a>オーバー ロードの利点  
 プロシージャのオーバー ロードの利点は、呼び出しの柔軟性です。 使用する、`post`プロシージャ宣言の前の例では、呼び出し元のコードは、いずれか、顧客 id を取得できます、`String`または`Integer`、いずれの場合も同じ手順を呼び出します。 次に例を示します。  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [方法: 複数のバージョンのプロシージャを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)
- [オーバーロードの解決](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
