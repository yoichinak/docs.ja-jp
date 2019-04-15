---
title: '方法: ローカライズされた日付/時刻情報を Web ユーザーに表示する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e97bc095332e626d79561ab5fdc7bad531e3ba31
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320159"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>方法: ローカライズされた日付/時刻情報を Web ユーザーに表示する
Web ページは世界中で表示されるため、ユーザーとの通信時の日時値の解析処理は、(通常は Web サーバーのローカル カルチャの形式である) 既定の形式には依存しないようにする必要があります。 代わりに、ユーザーが入力する日時文字列を処理する Web フォームで、ユーザーの優先カルチャで文字列が解析されるようにする必要があります。 同様に、日時データは、ユーザーのカルチャに準拠する形式でユーザーに表示されるようにする必要があります。 このトピックでは、その方法について説明します。  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>ユーザー入力の日時を解析するには  
  
1. <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> プロパティから返された文字列の配列に入力があるか判断します。 ない場合、手順 6 に進みます。  
  
2. <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列に入力がある場合、最初の要素を取得します。 最初の要素は、ユーザーの既定または優先する言語および地域です。  
  
3. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> コンストラクターを呼び出して、ユーザーの優先するカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化します。  
  
4. 変換の試行に <xref:System.DateTime> または <xref:System.DateTimeOffset> 型の `TryParse` または `Parse` メソッドのいずれかを呼び出します。 `provider` パラメーターを指定して、`TryParse` または `Parse` メソッドのオーバー ロードを使用し、次のいずれかを渡します。  
  
    -   手順 3 で作成した <xref:System.Globalization.CultureInfo> オブジェクト。  
  
    -   手順 3 で作成した <xref:System.Globalization.CultureInfo> オブジェクトの <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> プロパティによって返された <xref:System.Globalization.DateTimeFormatInfo> オブジェクト。  
  
5. 変換に失敗する場合、<xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列内のそれぞれの残りの要素に対して、手順 2 から 4 を繰り返します。  
  
6. それでも変換が失敗する場合や <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列が空の場合、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> プロパティによって返される、インバリアント カルチャを使用して文字列を解析します。  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>ユーザーの要求内のローカルの日時を解析するには  
  
1. Web フォームに、<xref:System.Web.UI.WebControls.HiddenField> コントロールを追加します。  
  
2. 協定世界時 (UTC) の現在の日時とローカルのタイム ゾーンのオフセットを <xref:System.Web.UI.WebControls.HiddenField.Value%2A> プロパティに記述し、`Submit` ボタンの `onClick` イベントを処理する JavaScript 関数を作成します。 (セミコロンなどの) 区切り記号を使用して、文字列の 2 つのコンポーネントを区切ります。  
  
3. Web フォームの <xref:System.Web.UI.Control.PreRender> イベントを使用し、スクリプトのテキストを <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> メソッドに渡して、関数を HTML 出力ストリームに挿入します。  
  
4. JavaScript 関数の名前を `Submit` ボタンの `OnClientClick` 属性に渡し、イベント ハンドラーを、`Submit` ボタンの `onClick` イベントに接続します。  
  
5. `Submit` ボタンの <xref:System.Web.UI.WebControls.Button.Click> イベントのハンドラーを作成します。  
  
6. イベント ハンドラーで、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> プロパティから返された文字列の配列に入力があるか判断します。 ない場合、手順 14 に進みます。  
  
7. <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列に入力がある場合、最初の要素を取得します。 最初の要素は、ユーザーの既定または優先する言語および地域です。  
  
8. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> コンストラクターを呼び出して、ユーザーの優先するカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化します。  
  
9. <xref:System.Web.UI.WebControls.HiddenField.Value%2A> プロパティに割り当てられた文字列を <xref:System.String.Split%2A> メソッドに渡し、ユーザーの文字列形式のローカルの日時と文字列形式のユーザーのローカル タイム ゾーン オフセットを別の配列要素に格納します。  
  
10. <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> または <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> メソッドのいずれかを呼び出し、ユーザーの要求の日時を <xref:System.DateTime> 値に変換します。 `provider` パラメーターを指定してメソッドのオーバー ロードを使用し、次のいずれかを渡します。  
  
    -   手順 8 で作成した <xref:System.Globalization.CultureInfo> オブジェクト。  
  
    -   手順 8 で作成した <xref:System.Globalization.CultureInfo> オブジェクトの <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> プロパティによって返された <xref:System.Globalization.DateTimeFormatInfo> オブジェクト。  
  
11. 手順 10 の解析操作に失敗した場合は、手順 13 に進みます。 それ以外の場合、<xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> メソッドを呼び出し、文字列形式のユーザーのタイム ゾーン オフセットを整数に変換します。  
  
12. <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> コンストラクターを呼び出して、ユーザーのローカル時間を表す <xref:System.DateTimeOffset> をインスタンス化します。  
  
13. 手順 10 で変換に失敗した場合、<xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列内のそれぞれの残りの要素に対して、手順 7 から 12 を繰り返します。  
  
14. それでも変換が失敗する場合や <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列が空の場合、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> プロパティによって返される、インバリアント カルチャを使用して文字列を解析します。 次いで手順 7 ～ 12 を繰り返します。  
  
 結果として、Web ページのユーザーのローカルの時間を表す <xref:System.DateTimeOffset> オブジェクトが生成されます。 その後、<xref:System.DateTimeOffset.ToUniversalTime%2A> メソッドを呼び出して、同等の UTC を判断することもできます。 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> メソッドを呼び出し、時間を変換するタイム ゾーンとして <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> の値を渡すことにより、Web サーバーの同等の日時を判断することも可能です。  
  
## <a name="example"></a>例  
 次の例には、ユーザーに日時の値の入力を求める、HTML ソースと ASP.NET Web フォームのコードの両方が含まれています。 クライアント側のスクリプトからも、ユーザー要求のローカルの日時と、ユーザーのタイム ゾーンのオフセットが、UTC から隠しフィールドに書き込まれます。 この情報は、その後サーバーによって解析され、ユーザー入力を表示する Web ページが返されます。 ユーザーのローカル時間、サーバーの時間、および UTC を使用して、ユーザーの要求の日時も表示されます。  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 クライアント側スクリプトは、JavaScript `toLocaleString` メソッドを呼び出します。 これにより、サーバー上で正常に解析される可能性が高い、ユーザーのロケールの書式指定規則に従う文字列が生成されます。  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> プロパティは、HTTP 要求に含まれる `Accept-Language` ヘッダーに含まれるカルチャ名から入力されます。 ただし、すべてのブラウザー要求には `Accept-Language` ヘッダーが含まれておらず、ユーザーがヘッダーを完全に抑制することも可能です。 これにより、ユーザー入力を解析するときに、フォールバック カルチャがあることが重要になります。 通常、フォールバック カルチャとは、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> によって返されるインバリアント カルチャです。 ユーザーが Internet Explorer のテキスト ボックスにカルチャ名を入力する場合もありますが、このとき、カルチャ名が無効である場合もあります。 これにより、<xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化するとき、例外処理を使用することが重要になります。  
  
 Internet Explorer が送信した HTTP 要求から取得した場合、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 配列はユーザーの優先順位に従って入力されます。 配列の最初の要素には、ユーザーのプライマリ カルチャまたは地域名があります。 配列に追加項目が含まれている場合、Internet Explorer はそれらに任意の品質指定子を割り当てます (これは、カルチャ名とセミコロンで区切られています)。 たとえば、fr-FR カルチャのエントリの形式は `fr-FR;q=0.7` となるなどです。  
  
 この例は、`useUserOverride` パラメーターが `false` に設定された <xref:System.Globalization.CultureInfo.%23ctor%2A> コンストラクターを呼び出し、新しい <xref:System.Globalization.CultureInfo> オブジェクトを作成します。 これにより、カルチャ名がサーバーの既定のカルチャ名の場合、クラス コンストラクターによって作成される新しい <xref:System.Globalization.CultureInfo> オブジェクトにカルチャの既定の設定が含まれます。サーバーの **[地域と言語のオプション]** アプリケーションでオーバーライドされた設定は反映されません。 サーバーで設定がオーバーライドされた場合、その値がユーザーのシステムに残ったり、ユーザーの入力に反映されたりすることは通常はありえません。  
  
 この例では、日時の 2 つの文字列 (1 つはユーザー入力のものであり、他は隠しフィールドに格納されているもの) を解析するので、事前に必要な可能性のある <xref:System.Globalization.CultureInfo> オブジェクトを定義します。 これでは、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> プロパティによって返される要素数よりも 1 つ大きい、<xref:System.Globalization.CultureInfo> オブジェクトの配列が生成されます。 その後、各言語/地域識別文字列用に <xref:System.Globalization.CultureInfo> オブジェクトがインスタンス化され、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を表す <xref:System.Globalization.CultureInfo> オブジェクトもインスタンス化されます。  
  
 ユーザーの日時の文字列表現を <xref:System.DateTime> 値に変換するには、コードで <xref:System.DateTime.Parse%2A> または <xref:System.DateTime.TryParse%2A> メソッドのいずれかを呼び出すことができます。 1 回の解析操作には、Parse メソッドへの呼び出しが複数回必要な場合もあります。 その結果、解析処理が失敗した場合、`false` が返されるので、<xref:System.DateTime.TryParse%2A> メソッドの方が優れています。 対照的に、1 つの Web アプリケーションで <xref:System.DateTime.Parse%2A> メソッドで何度もスローされる例外を処理することは、非常に不経済です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードをコンパイルするには、コードビハインドなしに [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web ページを作成します。 次いで、すべての既存のコードが置換されるよう、例を Web ページにコピーします。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web ページには、次のコントロールが含まれている必要があります。  
  
-   <xref:System.Web.UI.WebControls.Label> コントロール。これはコードで参照されません。 その <xref:System.Web.UI.WebControls.TextBox.Text%2A> プロパティを "Enter a Number:\(数字を入力:\)" に設定します。  
  
-   `DateString` という名前の <xref:System.Web.UI.WebControls.TextBox> コントロール。  
  
-   `OKButton` という名前の <xref:System.Web.UI.WebControls.Button> コントロール。 その <xref:System.Web.UI.WebControls.Button.Text%2A> プロパティを "OK" に設定します。  
  
-   `DateInfo` という名前の <xref:System.Web.UI.WebControls.HiddenField> コントロール。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ユーザーが HTML ストリームにスクリプトを挿入する行為を防ぐために、サーバー応答でユーザー入力がエコーのように返されないようにしてください。 代わりに、<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> メソッドを利用して暗号化されるようにします。  
  
## <a name="see-also"></a>関連項目

- [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)
- [標準の日時書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [カスタム日時書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [日付と時刻文字列の解析](../../../docs/standard/base-types/parsing-datetime.md)
