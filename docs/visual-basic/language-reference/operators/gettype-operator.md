---
title: GetType 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592149"
---
# <a name="gettype-operator-visual-basic"></a>GetType 演算子 (Visual Basic)
指定された型の <xref:System.Type> オブジェクトを返します。 <xref:System.Type> オブジェクトは、プロパティ、メソッド、イベントなどの型に関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---|---|  
|`typename`|情報を必要とする型の名前。|  
  
## <a name="remarks"></a>コメント  
 `GetType` 演算子は、指定された `typename`の <xref:System.Type> オブジェクトを返します。 `typename`には、定義されている型の名前を渡すことができます。 次に例を示します。  
  
- `Boolean` や `Date`などの Visual Basic のデータ型。  
  
- .NET Framework クラス、構造体、モジュール、またはインターフェイス (<xref:System.ArgumentException?displayProperty=nameWithType> や <xref:System.Double?displayProperty=nameWithType>など)。  
  
- アプリケーションで定義されている任意のクラス、構造体、モジュール、またはインターフェイス。  
  
- アプリケーションで定義されている任意の配列。  
  
- アプリケーションで定義されている任意のデリゲート。  
  
- Visual Basic、.NET Framework、またはアプリケーションによって定義された任意の列挙体。  
  
 オブジェクト変数の型オブジェクトを取得する場合は、<xref:System.Type.GetType%2A?displayProperty=nameWithType> メソッドを使用します。  
  
 `GetType` 演算子は、次のような場合に役立ちます。  
  
- 実行時には、型のメタデータにアクセスする必要があります。 <xref:System.Type> オブジェクトは、型のメンバーや配置情報などのメタデータを提供します。 これは、たとえば、アセンブリを反映するために必要です。 詳細については、「 <xref:System.Reflection?displayProperty=nameWithType>」を参照してください。  
  
- 2つのオブジェクト参照を比較して、同じ型のインスタンスを参照しているかどうかを確認します。 存在する場合、`GetType` は同じ <xref:System.Type> オブジェクトへの参照を返します。  
  
## <a name="example"></a>例  
 次の例は、使用されている `GetType` 演算子を示しています。  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>参照

- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
