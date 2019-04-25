---
title: その他のデータ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 4808d87322d5b21b70ec38e2eb31b2b204938745
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821766"
---
# <a name="miscellaneous-data-types-visual-basic"></a>その他のデータ型 (Visual Basic)
Visual Basic ではない数字や文字を対象とするいくつかのデータ型が用意されています。 代わりに、それらを扱う特化されたデータなど、はい/いいえ値、日付/時刻値、およびオブジェクトのアドレス。  
  
 Visual Basic のデータ型のサイド バイ サイドで比較を示す表を参照してください[データ型](../../../../visual-basic/language-reference/data-types/index.md)します。  
  
## <a name="boolean-type"></a>ブール型  
 [ブール データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)符号なしの値として解釈されるは`True`または`False`します。 データのサイズは実装されているプラットフォームに依存します。 場合は、変数は、はい/いいえ、またはオン/オフ、true または false などの 2 つの状態値のみを含めることができます、宣言として`Boolean`します。  
  
## <a name="date-type"></a>日付型  
 [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)は日付と時刻の両方の情報を保持する 64 ビット値です。 各インクリメントは、(12時 00分 AM) を開始してから、グレゴリオ暦での 1 年 1 月 1 日の経過時間の 100 ナノ秒を表します。 場合は、変数には、日付の値を時間の値、またはその両方を含めることができます、宣言として`Date`します。  
  
## <a name="object-type"></a>オブジェクトの型  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)は、アプリケーション内、またはその他のアプリケーションでオブジェクトのインスタンスを指す 32 ビット アドレスです。 `Object`変数は、アプリケーションが認識されると、任意のオブジェクトや任意のデータ型のデータに参照できます。 両方が含まれます*値の型*など`Integer`、 `Boolean`、および構造体のインスタンスと*参照型*、オブジェクトなどのクラスから作成されたのインスタンスである`String`と<xref:System.Windows.Forms.Form>のインスタンスの配列。  
  
 変数は、コンパイル時に不明なクラスのインスタンスへのポインターを格納する場合、またはさまざまなデータ型のデータを指すことができる場合は、宣言として`Object`します。  
  
 利点、`Object`データ型は、任意のデータ型のデータの格納に使用できます。 デメリットは、実行時間がかかると、アプリケーションの実行速度が遅く、余分な処理が発生することです。 使用する場合、`Object`発生する値の型の変数、*ボックス化*と*ボックス化解除*します。 に参照型を使用する場合に発生する*遅延バインディング*します。  
  
## <a name="see-also"></a>関連項目

- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [数値のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
