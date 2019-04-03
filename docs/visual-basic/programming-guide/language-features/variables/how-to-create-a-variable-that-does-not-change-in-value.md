---
title: '方法: 値 (Visual Basic) 変化しない変数を作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 57792db826caa996e163bc0a51b01a6bbd6a4858
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823325"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>方法: 値 (Visual Basic) 変化しない変数を作成します。
矛盾する値を変更しない変数の概念があります。 定数では不可能である場合もありますし、固定値を持つ変数を使用すると便利です。 このような場合でメンバー変数を定義することができます、 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)キーワード。  
  
 使用することはできません、 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)宣言を次の状況で定数の値を割り当てます。  
  
-   `Const`ステートメントには、使用するデータ型は受け入れません。  
  
-   コンパイル時に、値がわからない  
  
-   コンパイル時に定数値を計算できません。  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>値の変わらない変数を作成するには  
  
1.  モジュール レベルでのメンバー変数を宣言、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、含めると、 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)キーワード。  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     指定できる`ReadOnly`メンバー変数でのみです。 つまり、すべてのプロシージャの外部でのモジュール レベル変数を定義する必要があります。  
  
2.  コンパイル時に単一のステートメントで値を計算することができる場合は、初期化句を使用して、`Dim`ステートメント。 に従って、[として](../../../../visual-basic/language-reference/statements/as-clause.md)句に等号 (`=`)、その後に式。 コンパイラが定数の値には、この式を評価してください。  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     値を割り当てることができます、`ReadOnly`変数の 1 回だけです。 そうとコードはこれまでこの値を変更します。  
  
     、コンパイル時に、値がわからないするか、または単一のステートメントでは、コンパイル時に計算できない場合は、コンス トラクターで実行時にも割り当てることができます。 これを行うには、宣言する必要があります、`ReadOnly`クラスまたは構造体のレベルにある変数です。 そのクラスまたは構造体のコンス トラクターで変数の固定値を計算し、コンス トラクターから戻る前に、変数に割り当てます。  
  
## <a name="see-also"></a>関連項目

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)
