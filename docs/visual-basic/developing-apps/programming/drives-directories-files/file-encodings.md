---
title: ファイル エンコーディング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: d73226c58d39c970ec02c32a2c188f2747a7d87e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583463"
---
# <a name="file-encodings-visual-basic"></a>ファイル エンコーディング (Visual Basic)

ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキストを処理するときの文字の表現方法を指定します。 言語で処理できる (または処理できない) 文字という観点から、あるエンコードが他のエンコーディングよりも望ましいということがありますが、一般的には Unicode が好まれます。

ファイルに対する読み取りと書き込みでは、ファイル エンコーディングが適切に一致しないと、例外が発生したり、不正な結果となる場合があります。

## <a name="types-of-encodings"></a>エンコーディングの種類

ファイルを扱うときには、Unicode は最適なエンコーディングです。 Unicode は、世界共通の文字エンコーディング規則で、技術的な記号や出版で使用される特殊文字などを含む、現在のコンピューティングで使用されるすべての文字を、16 ビットのコード値で表します。

これまでの文字エンコーディング規則は、Windows ANSI 文字セットなどの従来からある文字セットで構成されており、8 ビットのコード値や 8 ビット値の組み合わせを使用して、特定の言語や地域で使用する文字を表していました。

## <a name="encoding-class"></a>Encoding クラス

<xref:System.Text.Encoding> クラスは文字エンコーディングを表します。 次の表は、利用可能なエンコーディングの型の一覧とそれぞれの説明です。

|name|説明|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Unicode 文字の ASCII 文字エンコードを表します。|
|<xref:System.Text.UnicodeEncoding>|Unicode 文字の UTF-16 エンコーディングを表します。|
|<xref:System.Text.UTF32Encoding>|Unicode 文字の UTF-32 エンコーディングを表します。|
|<xref:System.Text.UTF7Encoding>|Unicode 文字の UTF-7 エンコードを表します。|
|<xref:System.Text.UTF8Encoding>|Unicode 文字の UTF-8 エンコードを表します。|

## <a name="see-also"></a>関連項目

- [ファイルの読み取り](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [ファイルへの書き込み](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
