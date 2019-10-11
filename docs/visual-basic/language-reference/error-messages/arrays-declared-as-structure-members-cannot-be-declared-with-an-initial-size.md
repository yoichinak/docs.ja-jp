---
title: 構造体メンバーとして宣言された配列を初期サイズで宣言することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250151"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>構造体メンバーとして宣言された配列を初期サイズで宣言することはできません。

構造体の配列が初期サイズで宣言されています。 構造体要素を初期化することはできません。また、配列サイズの宣言は初期化の1つの形式です。

**エラー ID:** BC31043

## <a name="example"></a>例

次の例では、BC31043 が生成されます。

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 構造体の配列を動的として定義します (初期サイズはありません)。

2. 配列の特定のサイズが必要な場合は、コードの実行時に[ReDim ステートメント](../statements/redim-statement.md)を使用して動的配列を再作成できます。 次に例を示します。
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a>関連項目

- [配列](../../programming-guide/language-features/arrays/index.md)
- [2 つのオブジェクトが等しいかどうかをテストする方法構造体を宣言する](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
