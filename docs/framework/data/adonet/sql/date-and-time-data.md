---
title: 日付と時刻のデータ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: a4bbed1f115ef5cfb6b7b63156f2d84b071cf224
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127115"
---
# <a name="date-and-time-data"></a>日付と時刻のデータ
SQL Server 2008 では、日付と時刻の情報を扱うための新しいデータ型が導入されました。 新しいデータ型には、日付と時刻の別個のデータ型と、範囲、有効桁数、タイム ゾーン処理が向上した拡張データ型が含まれています。 .NET Framework 3.5 Service Pack (SP) 1 以降では、.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) が SQL Server 2008 データベース エンジンの新機能すべてをサポートします。 SqlClient でこれらの新機能を使用するには、.NET Framework 3.5 SP1 以降をインストールする必要があります。  
  
 SQL Server 2008 より前のバージョンの SQL Server では、日付と時刻に使用できるデータ型には `datetime` と `smalldatetime` の 2 つしかありませんでした。 どちらのデータ型も日付値と時刻値の両方を保持するため、日付と時刻のどちらか一方の値のみを使用するのが困難でした。 また、これらのデータ型でサポートされる日付は、英国で 1753 年にグレゴリオ暦が導入された後の日付に限られています。 もう 1 つの制限は、これらの古いデータ型はタイム ゾーンを処理できないことです。その結果、複数のタイム ゾーンから送られてくるデータの処理が難しくなっています。  
  
 SQL Server のデータ型に関する完全な説明は、SQL Server オンライン ブックに記載されています。 次の表は、バージョン別の日付と時刻のデータに関する初歩的なトピックの一覧です。  
  
 **SQL Server オンライン ブック**  
  
1.  [日時データの使用](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>SQL Server 2008 で導入された日付/時刻データ型  
 次の表は、新しい日付と時刻のデータ型の説明です。  
  
|SQL Server のデータ型|説明|  
|--------------------------|-----------------|  
|`date`|データ型 `date` の範囲は 01 年 1 月 1 日から 9999 年 12 月 31 日までで、精度は 1 日です。 既定値は 1900 年 1 月 1 日です。 記憶領域のサイズは 3 バイトです。|  
|`time`|`time` データ型は、24 時間形式で時刻値のみを格納します。 `time` データ型は、00:00:00.0000000 から 23:59:59.9999999 の範囲を 100 ナノ秒の精度で表すことができます。 既定値は 00:00:00.0000000 (午前 0 時) です。 `time` データ型はユーザー定義による 1 秒未満の時間の有効桁数をサポートし、記憶領域のサイズは、指定された有効桁数に応じて 3 バイト～ 6 バイトになります。|  
|`datetime2`|`datetime2` データ型は、`date` 型と `time` 型の範囲および有効桁数を単一のデータ型として組み合わせたものです。<br /><br /> 既定値および文字列リテラルの形式は、`date` 型および `time` 型で定義されているものと同じです。|  
|`datetimeoffset`|`datetimeoffset` データ型は、`datetime2` のすべての機能に加えて、タイム ゾーン オフセットを持ちます。 タイム ゾーン オフセットは、として表されます。 [+&#124;-] HH:MM。 HH は、タイム ゾーン オフセットの時間数を表す 00 ～ 14 の 2 桁の数字です。 MM は、タイム ゾーン オフセットの付加的な分数を表す 0 ～ 59 の 2 桁の数字です。 時刻の精度は 100 ナノ秒までサポートされます。 必須の + 記号または - 記号は、ローカル時刻を取得する際、UTC (協定世界時またはグリニッジ標準時) を基準としてタイム ゾーン オフセットを加算するか、減算するかを示します。|  
  
> [!NOTE]
>  `Type System Version` キーワードの使用方法の詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」を参照してください。  
  
## <a name="date-format-and-date-order"></a>日付書式と表記順序  
 SQL Server が日付と時刻の値をどのように処理するかは、型システムのバージョンとサーバーのバージョンだけでなく、サーバーの既定の言語と書式設定にも左右されます。 日付文字列が、ある言語の日付書式で有効な場合でも、別の言語と日付書式を使用している接続でクエリを実行した場合には意味を持たない可能性があります。  
  
 Transact-SQL の SET LANGUAGE ステートメントは、日付の構成要素の並べ方を決定する DATEFORMAT を暗黙に設定します。 日付構成要素の表記順序が MDY、DMY、YMD、YDM、MYD、DYM のいずれであるかを明確にするには、接続で Transact-SQL の SET DATEFORMAT ステートメントを使用します。  
  
 接続で DATEFORMAT を指定しないと、SQL Server はその接続に関連付けられている既定の言語を使用します。 たとえば、日付文字列 '01/02/03' は、言語が United States English に設定されているサーバーでは MDY (January 2, 2003) として、British English に設定されているサーバーでは DMY (February 1, 2003) として処理されます。 年は、SQL Server の終了年の規則に従って決定されます。この規則では、世紀の値を割り当てるための終了日が定義されます。 詳細については、次を参照してください。 [two digit year cutoff オプション](https://go.microsoft.com/fwlink/?LinkId=120473)SQL Server オンライン ブックの「します。  
  
> [!NOTE]
>  YDM 日付書式は、文字列形式から `date`、`time`、`datetime2`、または `datetimeoffset` に変換する場合にはサポートされません。  
  
 SQL Server が日付と時刻のデータを解釈する方法の詳細については、次を参照してください。[を使用して日付と時刻のデータ](https://go.microsoft.com/fwlink/?LinkID=98361)SQL Server 2008 オンライン ブックの「します。  
  
## <a name="datetime-data-types-and-parameters"></a>Date/Time データ型とパラメーター  
 新しい日付型と時刻型をサポートするために、<xref:System.Data.SqlDbType> には、次の列挙値が追加されています。  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  

データ型を指定することができます、 <xref:System.Data.SqlClient.SqlParameter> 、上記のいずれかを使用して<xref:System.Data.SqlDbType>列挙体。 

> [!NOTE]
> 設定することはできません、`DbType`のプロパティを`SqlParameter`に`SqlDbType.Date`します。

 <xref:System.Data.SqlClient.SqlParameter> オブジェクトの <xref:System.Data.SqlClient.SqlParameter.DbType%2A> プロパティを特定の `SqlParameter` 列挙値に設定することによって、<xref:System.Data.DbType> の型をジェネリックに指定することもできます。 <xref:System.Data.DbType> データ型と `datetime2` データ型をサポートするために、`datetimeoffset` には、次の列挙値が追加されています。  
  
-   DbType.DateTime2  
  
-   DbType.DateTimeOffset  
  
 これらの新しい列挙値は、以前のバージョンの .NET Framework に存在した `Date`、`Time`、および `DateTime` の各列挙値を補います。  
  
 パラメーター オブジェクトの .NET Framework データ プロバイダー型は、パラメーター オブジェクトの値の .NET Framework 型か、またはパラメーター オブジェクトの `DbType` から推論されます。 新しい date 型と time 型をサポートするための新しい <xref:System.Data.SqlTypes> データ型は導入されていません。 SQL Server 2008 の date 型/time 型と CLR のデータ型のマッピングを次の表に示します。  
  
|SQL Server のデータ型|.NET Framework 型|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.DateTime|日付|日付|  
|時間|System.TimeSpan|時刻|時刻|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter プロパティ  
 次の表は、日付と時刻のデータ型に関係する `SqlParameter` プロパティの説明です。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|値を NULL に設定できるかどうかを取得または設定します。 サーバーに NULL パラメーター値を送る場合は、<xref:System.DBNull> (Visual Basic の場合は `null`) ではなく、`Nothing` を指定する必要があります。 データベースの NULL 値の詳細については、「 [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)」を参照してください。|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|その値の最大桁数を取得または設定します。 この設定値は date データ型と time データ型では無視されます。|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|値の時刻部分を解決して、小数点以下桁数を取得または`Time`、 `DateTime2`、および`DateTimeOffset`します。 既定値は 0 です。これは、実際の桁数が値から推論されてサーバーに送られることを意味します。|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|date データ型と time データ型では無視されます。|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|パラメーター値を取得または設定します。|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|パラメーター値を取得または設定します。|  
  
> [!NOTE]
>  時刻の値が 0 と 24 の間にない場合は、<xref:System.ArgumentException> がスローされます。  
  
### <a name="creating-parameters"></a>パラメーターの作成  
 作成することができます、<xref:System.Data.SqlClient.SqlParameter>オブジェクトまたは追加することで、コンス トラクターを使用して、<xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A>呼び出してコレクション、`Add`のメソッド、 <xref:System.Data.SqlClient.SqlParameterCollection>。 `Add` メソッドは、入力としてコンストラクター引数または既存のパラメーター オブジェクトを受け取ります。  
  
 このトピックの次のセクションでは、日付と時刻のパラメーターを指定する方法の例を示します。 パラメーターの使用方法の例については、次を参照してください。[構成パラメーターとパラメーターのデータ型](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)と[DataAdapter パラメーター](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)します。  
  
### <a name="date-example"></a>Date の例  
 次のコード フラグメントは、`date` パラメーターの指定方法を示しています。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Time の例  
 次のコード フラグメントは、`time` パラメーターの指定方法を示しています。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Datetime2 の例  
 次のコード フラグメントは、`datetime2` パラメーターの日付と時刻の指定方法を示しています。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>DateTimeOffSet の例  
 次のコード フラグメントは、`DateTimeOffSet` パラメーターの日付と時刻、およびタイム ゾーン オフセット 0 を指定する方法を示しています。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
 次のコード フラグメントのように、`AddWithValue` の <xref:System.Data.SqlClient.SqlCommand> メソッドを使用してパラメーターを渡すこともできます。 ただし、`AddWithValue` メソッドでは <xref:System.Data.SqlClient.SqlParameter.DbType%2A> または <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> をパラメーターに指定できません。  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date`パラメーターにマップできます、 `date`、 `datetime`、または`datetime2`サーバー上のデータ型。 新しい `datetime` データ型を使用するときは、パラメーターの <xref:System.Data.SqlDbType> プロパティをそのインスタンスのデータ型に明示的に設定する必要があります。 <xref:System.Data.SqlDbType.Variant> の使用やパラメーター値の明示的な指定により、`datetime` および `smalldatetime` データ型との下位互換性の問題が発生する場合があります。  
  
 次の表は、どの `SqlDbTypes` がどの CLR 型から推論されるかを示しています。  
  
|CLR 型|推論される SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>日付と時刻データの取得  
 SQL Server 2008 の日付値および時刻値を取得するためのメソッドを次の表に示します。  
  
|SqlClient のメソッド|説明|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|指定された列の値を <xref:System.DateTime> 構造体として取得します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|指定された列の値を <xref:System.DateTimeOffset> 構造体として取得します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|特定のフィールドについて、基になるプロバイダー固有の型を返します。 新しい date 型および time 型については、`GetFieldType` と同じ型が返されます。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|指定された列の値を取得します。 新しい date 型および time 型については、`GetValue` と同じ型が返されます。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|指定された配列の値を取得します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|列の値を <xref:System.Data.SqlTypes.SqlString> として取得します。 データを <xref:System.InvalidCastException> で表現できない場合、`SqlString` が発生します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|列データを対応する既定の `SqlDbType` として取得します。 新しい date 型および time 型については、`GetValue` と同じ型が返されます。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|指定された配列の値を取得します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Type System Version が SQL Server 2005 に設定されている場合、列の値を文字列として取得します。 データを文字列で表現できない場合、<xref:System.InvalidCastException> が発生します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|指定された列の値を <xref:System.TimeSpan> 構造体として取得します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|指定された列の値を、基になる CLR 型として取得します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|配列内の列の値を取得します。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|結果セットのメタデータを表す <xref:System.Data.DataTable> を返します。|  
  
> [!NOTE]
>  新しい日付と時刻の `SqlDbTypes` は、SQL Server 内でインプロセスで実行されるコードではサポートされません。 そのような型の 1 つがサーバーに渡されると、例外が発生します。  
  
## <a name="specifying-date-and-time-values-as-literals"></a>日付値と時刻値のリテラル指定  
 日付と時刻のデータ型は、さまざまなリテラル文字列形式を使用して指定できます。SQL Server は、実行時にそれらを内部の日付/時刻構造体に変換します。 SQL Server は、単一引用符 (') で囲まれた日付と時刻のデータを認識します。 次に文字列形式の例を示します。  
  
-   英数字の日付書式 (`'October 15, 2006'` など)。  
  
-   数字の日付書式 (`'10/15/2006'` など)。  
  
-   区切りなしの文字列形式 (`'20061015'` など)。これは ISO 規格の日付書式では 2006 年 10 月 15 日と解釈されます。  
  
> [!NOTE]
>  すべてのリテラル文字列形式と日付/時刻データ型のその他の特徴については、SQL Server オンライン ブックに完全な説明が記載されています。  
  
 時刻の値が 0 と 24 の間にない場合は、<xref:System.ArgumentException> がスローされます。  
  
## <a name="resources-in-sql-server-2008-books-online"></a>SQL Server 2008 オンライン ブックの関連トピック  
 SQL Server 2008 での日付値と時刻値の使用方法の詳細については、SQL Server 2008 オンライン ブックで次の関連トピックを参照してください。  
  
|トピック|説明|  
|-----------|-----------------|  
|[日付と時刻のデータ型および関数 (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Transact-SQL の日付と時刻のデータ型および関数の概要について説明します。|  
|[日時データの使用](https://go.microsoft.com/fwlink/?LinkId=98361)|日付と時刻のデータ型と関数の情報、および使用例を示します。|  
|[データ型 (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|SQL Server 2008 のシステム データ型について説明します。|  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型のマッピング](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [パラメーターおよびパラメーター データ型の構成](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [SQL Server データ型と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
