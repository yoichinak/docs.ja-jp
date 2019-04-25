---
title: 属性リスト (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 2399ec1342280df101e2818399e0f41f10d9606d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818421"
---
# <a name="attribute-list-visual-basic"></a>属性リスト (Visual Basic)
宣言されたプログラミング要素に適用される属性を指定します。 複数の属性を指定するときは、コンマで区切ります。 1 つの属性の構文を次に示します。  
  
## <a name="syntax"></a>構文  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>指定項目  
|||
|---|---|
|`attributemodifier`|ソース ファイルの先頭に適用される属性に必要です。 [アセンブリ](../../../visual-basic/language-reference/modifiers/assembly.md)または[モジュール](../../../visual-basic/language-reference/modifiers/module-keyword.md)します。|
|`attributename`| 必須。 属性の名前。|
|`attributearguments`|省略可能です。 この属性の位置指定引数のリスト。 複数の引数は、コンマで区切られます。|
|`attributeinitializer`|省略可能です。 この属性の変数またはプロパティの初期化子の一覧です。 複数の初期化子は、コンマで区切られます。|
  
## <a name="remarks"></a>Remarks  
 ほぼすべてのプログラミング要素 (型、プロシージャ、プロパティ、およびなど) には、1 つまたは複数の属性を適用できます。 属性がアセンブリのメタデータに表示され、コードの注釈を設定または特定のプログラミング要素を使用する方法を指定するのに役立ちます。 Visual Basic と .NET Framework によって定義された属性を適用して、独自の属性を定義することができます。  

 属性を使用する場合の詳細については、次を参照してください。[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)します。 属性名には、次を参照してください。 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
## <a name="rules"></a>ルール  
  
-   **配置。** 最も宣言されたプログラミング要素に属性を適用することができます。 配置する 1 つまたは複数の属性を適用する、*属性ブロック*要素宣言の先頭にします。 属性リストの各エントリには、適用する属性および修飾子と属性のこの呼び出しを使用する引数を指定します。  
  
-   **山かっこします。** 属性リストを指定する場合は、山かっこで囲む必要があります ("`<`「と」`>`")。  
  
-   **宣言の一部です。** 属性は、個別のステートメントではなく、要素の宣言の一部である必要があります。 行連結シーケンスを使用することができます (" `_`") を複数のソース コード行に、宣言ステートメントを拡張します。  
  
-   **修飾子。** 属性の修飾子 (`Assembly`または`Module`) ソース ファイルの先頭のプログラミング要素に適用する属性が必要です。 ソース ファイルの先頭になっている要素に適用される属性では、属性の修飾子は使用できません。  
  
-   **引数。** 属性のすべての位置指定引数には、任意の変数またはプロパティの初期化子が前にする必要があります。  
  
## <a name="example"></a>例  
 次の例では、適用、<xref:System.Runtime.InteropServices.DllImportAttribute>属性のスケルトン定義を`Function`プロシージャ。  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 属性付きの手順がアンマネージ ダイナミック リンク ライブラリ (DLL) のエントリ ポイントを表すことを示します。 属性は、位置指定引数として DLL 名と変数の初期化子とその他の情報を提供します。  
  
## <a name="see-also"></a>関連項目

- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Module \<キーワード>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [方法: コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
