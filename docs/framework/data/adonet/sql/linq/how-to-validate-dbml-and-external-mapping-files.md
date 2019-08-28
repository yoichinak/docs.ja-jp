---
title: '方法: DBML ファイルおよび外部マッピング ファイルを検証する'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041142"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>方法: DBML ファイルおよび外部マッピング ファイルを検証する

変更した外部マッピング ファイルや .dbml ファイルは、それぞれのスキーマ定義に対して検証する必要があります。 このトピックでは、Visual Studio ユーザーが検証プロセスを実装する手順について説明します。

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a>.dbml ファイルまたは XML ファイルを検証するには

1. Visual Studio の **[ファイル]** メニューで、 **[開く]** をポイントし、 **[ファイル]** をクリックします。

2. **[ファイルを開く]** ダイアログボックスで、検証する .dbml ファイルまたは XML マッピングファイルをクリックします。

    **XML エディター**でファイルが開きます。

3. ウィンドウを右クリックし、 **[プロパティ]** をクリックします。

4. **[プロパティ]** ウィンドウで、 **[スキーマ]** プロパティの省略記号をクリックします。

    **[XML スキーマ]** ダイアログボックスが表示されます。

5. 目的に適したスキーマ定義を見つけます。

    - DbmlSchema.xsd は、.dbml ファイルを検証するためのスキーマ定義です。 詳細については、「 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)」を参照してください。

    - LinqToSqlMapping.xsd は、外部 XML マッピング ファイルを検証するためのスキーマ定義です。 詳細については、「[外部マッピング](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)」を参照してください。

6. 目的のスキーマ定義行の **[使用]** 列で、をクリックしてドロップダウンボックスを開き、 **[このスキーマを使用]** する をクリックします。

    これで、スキーマ定義ファイルが DBML ファイルまたは XML マッピング ファイルに関連付けられます。

    他のスキーマ定義は選択しないようにしてください。

7. **[表示]** メニューの **[エラー一覧]** をクリックします。

    エラー、警告、またはメッセージが生成されていないか確認します。 生成されていなければ、XML ファイルはスキーマ定義に対して有効です。

## <a name="alternate-method-for-supplying-schema-definition"></a>スキーマ定義を指定する別の方法

何らかの理由で適切な .xsd ファイルが **[XML スキーマ]** ダイアログボックスに表示されない場合は、ヘルプトピックから .xsd ファイルをダウンロードできます。 次の手順は、Visual Studio XML エディターで必要な Unicode 形式でダウンロードしたファイルを保存するのに役立ちます。

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>スキーマ定義ファイルをヘルプ トピックからコピーするには

1. このトピックで既に説明したように、スキーマ定義が含まれているヘルプ トピックを表示します。

    - .Dbml ファイルについては、「 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)」を参照してください。

    - 外部マッピングファイルについては、「[外部マッピング](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)」を参照してください。

2. コードファイルをクリップボードにコピーするには、 **[コードのコピー]** をクリックします。

3. メモ帳を起動して、新しいファイルを作成します。

4. クリップボードからメモ帳のファイルにコードを貼り付けます。

5. メモ帳の **[ファイル]** メニューの 名前を付け **[て保存]** をクリックします。

6. **[エンコード]** ボックスで、 **[Unicode]** を選択します。

    > [!IMPORTANT]
    > これを選択することで、テキスト ファイルの先頭に Unicode-16 のバイト順マーカー (`FFFE`) が追加されます。

7. **[ファイル名]** ボックスに、拡張子が .xsd のファイル名を作成します。

## <a name="see-also"></a>関連項目

- [参照](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
