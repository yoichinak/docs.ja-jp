---
title: 列挙型を使用する状況 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825106"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>列挙型を使用する状況 (Visual Basic)
列挙体は、関連する定数のセットを操作する簡単な方法を提供します。 列挙型で、または`Enum`一連の値のシンボリック名です。 列挙体は、データ型として扱われ、それらを使用して、変数とプロパティを使用するための定数のセットを作成することができます。  
  
## <a name="when-to-use-an-enumeration"></a>列挙型を使用する状況  
 プロシージャが限られた一連の変数を受け取ったときは、列挙体の使用を検討します。 列挙体は、わかりやすい名前を使用する場合に特にわかりやすく読みやすいコードのこと。  
  
 列挙体を使用する利点は次のとおりです。  
  
-   置き換えや数値の入力ミスによって発生したエラーを軽減します。  
  
-   簡単に、将来の値を変更します。  
  
-   により、コードを読みやすくするので、そこにエラーが生じる可能性がある可能性が低くなります。  
  
-   前方の互換性を確保します。 列挙型をコードがメンバー名に対応する値が、今後だれかが変更された場合に失敗する可能性を低減します。  
  
## <a name="naming-enumerations"></a>名前付けの列挙型  
 列挙型メンバーの名前付け規則を使用します。 Visual Basic では、列挙体のメンバー名が検出されると、他の参照先のタイプ ライブラリには、同じ名前が含まれている場合に例外がスローする可能性があります。 アプリケーションまたはコンポーネントの値を識別する一意のプレフィックスを使用します。  
  
 列挙体のメンバーを指すときにする必要があります、列挙名でメンバー名を修飾を使用してください、`Imports`ステートメント。 詳細については、次を参照してください。[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)します。  
  
## <a name="predefined-enumerations"></a>定義済みの列挙型  
 Visual Basic では、多数の定義済みの列挙など`FirstDayOfWeek`と`MsgBoxResult`コードを容易にします。 これらの一覧については、次を参照してください。[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)します。  
  
## <a name="see-also"></a>関連項目

- [方法: 列挙体を宣言します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [方法: 列挙体のメンバーを参照してください。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
