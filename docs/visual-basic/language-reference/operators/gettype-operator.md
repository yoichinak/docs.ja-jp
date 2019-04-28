---
title: GetType 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 34ab192814583db5cdc0d0183c73cc22b8633e9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663610"
---
# <a name="gettype-operator-visual-basic"></a>GetType 演算子 (Visual Basic)
返します、<xref:System.Type>指定した型のオブジェクト。 <xref:System.Type>オブジェクトなど、そのプロパティ、メソッド、およびイベントの種類に関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---|---|  
|`typename`|情報を取得する対象の型の名前。|  
  
## <a name="remarks"></a>Remarks  
 `GetType`演算子を返します、<xref:System.Type>指定したオブジェクト`typename`します。 定義済みのすべての種類の名前を渡すことができます`typename`します。 次に例を示します。  
  
- などの任意の Visual Basic データ入力`Boolean`または`Date`します。  
  
- .NET Framework クラス、構造体、モジュール、またはインターフェイスなど<xref:System.ArgumentException?displayProperty=nameWithType>または<xref:System.Double?displayProperty=nameWithType>します。  
  
- クラス、構造体、モジュール、またはアプリケーションによって定義されたインターフェイス。  
  
- アプリケーションで定義されている配列。  
  
- アプリケーションで定義されているすべてのデリゲート。  
  
- Visual Basic、.NET Framework、またはアプリケーションによって定義されたすべての列挙体。  
  
 オブジェクト変数の型のオブジェクトを取得する場合は、使用、<xref:System.Type.GetType%2A?displayProperty=nameWithType>メソッド。  
  
 `GetType`演算子は、次の状況で役に立ちます。  
  
- 型のメタデータは、実行時にアクセスする必要があります。 <xref:System.Type>オブジェクト型のメンバーおよび展開の情報などのメタデータを提供します。 必要があります、たとえば、アセンブリを反映するようにします。 詳細については、「 <xref:System.Reflection?displayProperty=nameWithType> 」を参照してください。  
  
- 同じ型のインスタンスを参照しているかどうかを 2 つのオブジェクト参照を比較します。 場合は、`GetType`同じへの参照を返します<xref:System.Type>オブジェクト。  
  
## <a name="example"></a>例  
 次の例に示す、`GetType`演算子を使用します。  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
