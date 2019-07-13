---
title: ADO.NET での接続文字列
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 3b7cb0ab061da8364a9fecc3868ba9aaf7501577
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881162"
---
# <a name="connection-strings-in-adonet"></a>ADO.NET での接続文字列

接続文字列には、データ プロバイダーからデータ ソースにパラメーターとして渡す初期化情報が含まれています。 データ プロバイダーの値として、接続文字列を受け取る、<xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>プロパティ。 プロバイダーは、接続文字列を解析し、により、構文が正しいことと、キーワードがサポートされていること。 次に、<xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType>メソッドは、データ ソースに解析された接続パラメーターを渡します。 データ ソースは、さらに検証を実行し、接続を確立します。

## <a name="connection-string-syntax"></a>接続文字列の構文

接続文字列は、パラメーターのキー/値ペアのセミコロンで区切られた一覧を示します。

```
keyword1=value; keyword2=value;
```

キーワードは区別されません。 値、ただし、可能性があります、データ ソースによって、大文字小文字が区別されます。 キーワードと値の両方を含めることができます[空白文字](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)します。 先頭および末尾の空白文字がキーワードで無視され、引用符の値。

値には、セミコロンが含まれている場合[Unicode コントロール文字](https://en.wikipedia.org/wiki/Unicode_control_characters)、先頭または末尾の空白文字、単一引用符または二重引用符で囲む必要がありますか。 例:

```
Keyword=" whitespace  ";
Keyword='special;character';
```

それを囲む文字を囲む値内で発生しません。 そのため、単一引用符を含む値を囲む二重引用符でのみ、またはその逆ことができます。

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

、等号と同様に、引用符は不要、エスケープため、次の接続文字列が無効です。

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

後者の例の値は、各値は、[次へ] のセミコロンまたは文字列の末尾まで読み取ることが、ため`a=b=c`、最後のセミコロンは省略可能です。

すべての接続文字列は、上記で説明した同じ基本的な構文を共有します。 認識されているキーワードのセットは、ただしは、プロバイダーに依存しなど、以前の Api から長年にわたって進化してきた*ODBC*します。 *.NET Framework*用データ プロバイダーの*SQL Server* (`SqlClient`) 従来の Api から多くのキーワードをサポートしていますが、一般より柔軟な一般的な接続文字列の多くのシノニムを受け入れる、キーワード。

入力ミス エラーが発生することができます。 たとえば、`Integrated Security=true`が有効では`IntegratedSecurity=true`エラーが発生します。

未検証のユーザー入力からの実行時に手動で構築された接続文字列は、文字列のインジェクション攻撃に対して脆弱なし、データ ソースでセキュリティを損ないます。 これらの問題に対処する*ADO.NET* 2.0 で[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)各 *.NET Framework*データ プロバイダー。 これらの接続文字列ビルダーは、厳密に型指定されたプロパティとしてパラメーターを公開し、データ ソースに送信される前に、接続文字列を検証すること。

## <a name="in-this-section"></a>このセクションの内容

[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)\
`ConnectionStringBuilder` クラスを使用して、有効な接続文字列を実行時に作成する方法について説明します。

[接続文字列と構成ファイル](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\
構成ファイルを使用した接続文字列の格納と取得の方法について説明します。

[接続文字列の構文](../../../../docs/framework/data/adonet/connection-string-syntax.md)\
`SqlClient`、`OracleClient`、`OleDb`、`Odbc` の各プロバイダーに固有の接続文字列を構成する方法について説明します。

[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)\
データ ソースへの接続に使用する情報を保護する方法を示します。

## <a name="see-also"></a>関連項目

- [データ ソースへの接続](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
