---
title: その他のデータ型
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: cc6262b5bb305bb839917e222d831fa3340a1b14
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346342"
---
# <a name="miscellaneous-data-types-visual-basic"></a>その他のデータ型 (Visual Basic)
Visual Basic には、数値や文字を対象としていない複数のデータ型が用意されています。 これらは、yes/no の値、日付/時刻の値、オブジェクト アドレスなど、特殊なデータを扱います。  
  
 Visual Basic データ型を並べて比較している表を、[データ型](../../../../visual-basic/language-reference/data-types/index.md)に関するページで参照してください。  
  
## <a name="boolean-type"></a>ブール型  
 [Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)は、`True` または `False` と解釈される符号なしの値です。 データ幅は、実装するプラットフォームによって異なります。 変数が 2 つの状態 (true/false、yes/no、on/off など) の値のみを含む可能性がある場合は、`Boolean` として宣言します。  
  
## <a name="date-type"></a>日付型  
 [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)は、日付と時刻の両方の情報を保持する 64 ビット値です。 各インクリメントはグレゴリオ暦の西暦 1 年 1 月 1 日 (午前 12:00) からの経過時間を 100 ナノ秒単位で表します。 変数が日付値、時刻値、またはその両方を含む可能性がある場合は、`Date` として宣言します。  
  
## <a name="object-type"></a>オブジェクトの型  
 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)は、自らのアプリケーションまたはその他のアプリケーション内のオブジェクト インスタンスを指す 32 ビットのアドレスです。 `Object` 変数は、アプリケーションによって認識される任意のオブジェクト、または任意のデータ型のデータを参照できます。 これには、"*値型*" (`Integer`、`Boolean`、構造体インスタンスなど) と "*参照型*" (`String` や <xref:System.Windows.Forms.Form>などのクラスから作成されるオブジェクトのインスタンスおよび配列インスタンス) の両方が含まれます。  
  
 変数に含まれるポインターが、コンパイル時にはわからないクラスのインスタンスを指している場合、またはさまざまなデータ型の値を指す可能性がある場合は、`Object` として宣言します。  
  
 `Object` データ型の利点は、任意のデータ型のデータを格納するために使用できることです。 欠点は、実行時間が長くなる追加処理が発生し、アプリケーションのパフォーマンスが低下することです。 値型の `Object` 変数を使用すると、"*ボックス化*" と "*ボックス化解除*" が発生します。 参照型に対して使用すると、"*遅延バインディング*" が発生します。  
  
## <a name="see-also"></a>関連項目

- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [数値のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
