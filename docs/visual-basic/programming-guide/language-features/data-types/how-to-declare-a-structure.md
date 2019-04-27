---
title: '方法: 構造体 (Visual Basic) を宣言します。'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a52daddaa8701ccca9bd9b5b4a48535a6ffa19ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906712"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>方法: 構造体 (Visual Basic) を宣言します。
構造体の宣言を開始する、 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)、それを終了して、`End Structure`ステートメント。 これら 2 つのステートメントの間で、少なくとも 1 つを宣言する必要があります*要素*します。 任意のデータ型の要素ができますが、非共有変数または非共有の非カスタム イベントのいずれかに少なくとも 1 つである必要があります。  
  
 構造体の宣言で構造体の要素を初期化することはできません。 構造型の変数を宣言するときに、要素に、変数を通じてアクセスすることにより値を割り当てます。  
  
 構造体とクラス間の違いの詳細については、次を参照してください。[構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)します。  
  
 デモンストレーションを目的として、従業員の名前、電話の拡張機能と給与を追跡する必要がある状況を検討してください。 構造体を使用すると、1 つの変数でこれを行うことができます。  
  
### <a name="to-declare-a-structure"></a>構造体を宣言するには  
  
1. 最初と最後のステートメントの構造を作成します。  
  
     使用して、構造体のアクセス レベルを指定することができます、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、またはことことができます既定で`Public`します。  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2. 構造体の本文には、要素を追加します。  
  
     構造体には、少なくとも 1 つの要素が必要です。 すべての要素を宣言し、アクセス レベルを指定する必要があります。 使用する場合、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、キーワードを指定せずに既定でアクセシビリティ`Public`します。  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     `salary`フィールドが前の例で`Private`、つまりは外側のクラスからでも、構造体の外部アクセスできません。 ただし、`giveRaise`プロシージャが`Public`ので、構造体の外側から呼び出すことができます。 同様に、増やすことができます、`salaryReviewTime`構造の外からのイベント。  
  
     変数に加えて`Sub`プロシージャ、およびイベント、定数を定義することもできます。`Function`プロシージャ、および構造のプロパティ。 として最大で 1 つのプロパティを指定することができます、*プロパティの既定*、少なくとも 1 つの引数を受け取る。 イベントを処理することができます、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`プロシージャ。 詳細については、「[方法 :宣言し、Visual Basic では、既定のプロパティを呼び出す](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)します。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [構造体変数](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [構造体とその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [ユーザー定義型](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
