---
title: '方法: Web コントロールでの数値のユーザー入力を数値に変換する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f732f5bf61ed65fe7e62d110494d874262e30fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296161"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>方法: Web コントロールでの数値のユーザー入力を数値に変換する
Web ページは世界中のあらゆる場所で表示され、利用者はほぼ無限の形式で <xref:System.Web.UI.WebControls.TextBox> コントロールに数値データを入力できます。 結果として、Web ページの利用者の住んでいる地域 (ロケール) や文化 (カルチャ) を判断することが非常に重要となります。 ユーザー入力を解析するとき、ユーザーのロケールとカルチャによって定義される書式設定規則を適用できます。  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Web TextBox コントロールの数値入力を数字に変換するには  
  
1. <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> プロパティから返された文字列の配列に入力があるか判断します。 ない場合、手順 6 に進みます。  
  
2. <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列に入力がある場合、最初の要素を取得します。 最初の要素は、ユーザーの既定または優先する言語および地域です。  
  
3. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> コンストラクターを呼び出して、ユーザーの優先するカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化します。  
  
4. ユーザーの入力の変換後の形となる数値型の `TryParse` または `Parse` メソッドを呼び出します。 `provider` パラメーターを指定して `TryParse` または `Parse` メソッドのオーバー ロードを使用し、次のいずれかを渡します。  
  
    -   手順 3 で作成した <xref:System.Globalization.CultureInfo> オブジェクト。  
  
    -   手順 3 で作成した <xref:System.Globalization.CultureInfo> オブジェクトの <xref:System.Globalization.CultureInfo.NumberFormat%2A> プロパティによって返された <xref:System.Globalization.NumberFormatInfo> オブジェクト。  
  
5. 変換に失敗する場合、<xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列内のそれぞれの残りの要素に対して、手順 2 から 4 を繰り返します。  
  
6. それでも変換が失敗する場合や <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティから返された文字列の配列が空の場合、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> プロパティによって返される、インバリアント カルチャを使用して文字列を解析します。  
  
## <a name="example"></a>例  
 次は Web フォームの完全な分離コード ページの例です。<xref:System.Web.UI.WebControls.TextBox> コントロールに (アルファベットではなく) 数値を入力するように求め、それを数字に変換します。 数字に変換された後、元の入力と同じ書式設定ルールを利用して倍精度にして表示されます。  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> プロパティは、HTTP 要求に含まれる `Accept-Language` ヘッダーに含まれるカルチャ名から入力されます。 ただし、すべてのブラウザー要求には `Accept-Language` ヘッダーが含まれておらず、ユーザーがヘッダーを完全に抑制することも可能です。 これにより、ユーザー入力を解析するときに、フォールバック カルチャがあることが重要になります。 通常、フォールバック カルチャとは、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> によって返されるインバリアント カルチャです。 ユーザーが Internet Explorer のテキスト ボックスにカルチャ名を入力する場合もありますが、このとき、カルチャ名が無効である場合もあります。 これにより、<xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化するとき、例外処理を使用することが重要になります。  
  
 Internet Explorer が送信した HTTP 要求から取得した場合、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 配列はユーザーの優先順位に従って入力されます。 配列の最初の要素には、ユーザーのプライマリ カルチャまたは地域名があります。 配列に追加項目が含まれている場合、Internet Explorer はそれらに任意の品質指定子を割り当てます (これは、カルチャ名とセミコロンで区切られています)。 たとえば、fr-FR カルチャのエントリの形式は `fr-FR;q=0.7` となるなどです。  
  
 この例は、`useUserOverride` パラメーターが `false` に設定された <xref:System.Globalization.CultureInfo.%23ctor%2A> コンストラクターを呼び出し、新しい <xref:System.Globalization.CultureInfo> オブジェクトを作成します。 これにより、カルチャ名がサーバーの既定のカルチャ名の場合、クラス コンストラクターによって作成される新しい <xref:System.Globalization.CultureInfo> オブジェクトにカルチャの既定の設定が含まれます。サーバーの **[地域と言語のオプション]** アプリケーションでオーバーライドされた設定は反映されません。 サーバーで設定がオーバーライドされた場合、その値がユーザーのシステムに残ったり、ユーザーの入力に反映されたりすることは通常はありえません。  
  
 コードは、ユーザーの入力の変換後の形となる数値型の `Parse` または `TryParse` メソッドを呼び出すことができます。 1 回の解析操作には、Parse メソッドへの呼び出しが複数回必要な場合もあります。 その結果、解析処理が失敗した場合、`false` が返されるので、`TryParse` メソッドの方が優れています。 対照的に、1 つの Web アプリケーションで `Parse` メソッドで何度もスローされる例外を処理することは、非常に不経済です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードをコンパイルするには、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 分離コード ページにそれをコピーします。すべての既存コードが置換されます。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web には、次のコントロールを含めてください。  
  
-   <xref:System.Web.UI.WebControls.Label> コントロール。これはコードで参照されません。 その <xref:System.Web.UI.WebControls.TextBox.Text%2A> プロパティを "Enter a Number:\(数字を入力:\)" に設定します。  
  
-   `NumericString` という名前の <xref:System.Web.UI.WebControls.TextBox> コントロール。  
  
-   `OKButton` という名前の <xref:System.Web.UI.WebControls.Button> コントロール。 その <xref:System.Web.UI.WebControls.Button.Text%2A> プロパティを "OK" に設定します。  
  
 名前を `NumericUserInput` から、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページの `Page` ディレクティブの `Inherits` 属性によって定義されるクラスの名前に変更します。 `NumericInput` オブジェクト参照の名前を、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページの `form` タグの `id` 属性によって定義される名前に変更します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ユーザーが HTML ストリームにスクリプトを挿入する行為を防ぐために、サーバー応答でユーザー入力がエコーのように返されないようにしてください。 代わりに、<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> メソッドを利用して暗号化されるようにします。  
  
## <a name="see-also"></a>関連項目

- [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)
- [数値文字列の解析](../../../docs/standard/base-types/parsing-numeric.md)
