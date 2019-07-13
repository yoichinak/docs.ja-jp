---
title: FileName で指定されたファイルは、正しい XML ファイルではありません
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 5a54e5e7e7c75bb7d766b1bbda10f401fa8b99af
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640831"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>FileName で指定されたファイルは、正しい XML ファイルではありません

指定したファイル名は、正しい XML ファイルではありません。 XML ドキュメントの許可されている構造体とコンテンツを指定する場合、ドキュメント型定義 (DTD)、Microsoft XML-Data Reduced (XDR) スキーマ、または XML スキーマ定義言語 (XSD) スキーマを使用できます。 XSD スキーマは、.NET Framework で XML 文法を指定することをお勧めします。

> [!NOTE]
> Visual Studio の以前のバージョンにある **XML デザイナー** とは、型指定されたデータセットおよび XML スキーマのデザイナーのことです。 **XML デザイナー** は、XML スキーマ ファイルの作成と編集に今も使用できます。 ただし、Visual Studio 2012 では、型指定されたデータセットを作成および編集デザイナーは、**データセット デザイナー**します。 詳細については、次を参照してください。[の作成と型指定されたデータセットの編集](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120))します。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 正しいファイル名を指定していることを確認します。

- 確認する必要のある XML ファイルを **XML デザイナー**に読み込んで、指定したファイルに正しい XML が含まれていることを確認します。 **[XML]** メニューで、 **[XML の整合性チェック]** をクリックします。 エラーは **[タスク一覧]** に表示されます。

- XML ファイルに関連付けられた XML スキーマがある場合は、定義された構造体にその要素が出現し、個々の要素のコンテンツがスキーマで指定された宣言されたデータ型に準拠していることを確認します。

## <a name="see-also"></a>関連項目

- <xref:System.Xml>
- [方法: ファイル パスを解析する](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
