---
title: Visual Basic においてカルチャが文字列に与える影響
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d3c7ae9da9c18e53da393928e34dcfbf04fc891c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834622"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Visual Basic においてカルチャが文字列に与える影響
このヘルプ ページは、Visual Basic がカルチャ情報を使用して、文字列の変換との比較を実行する方法について説明します。  
  
## <a name="when-to-use-culture-specific-strings"></a>カルチャ固有の文字列を使用する場合  
 通常、カルチャに固有の文字列に示されているすべてのデータを使用してと、ユーザーからの読み取りをアプリケーションの内部データのカルチャで不変の文字列を使用する必要があります。  
  
 たとえばを文字列として日付を入力するユーザーを求めるアプリケーション、ユーザーが自分のカルチャに基づく文字列を書式設定ことが予想され、アプリケーションでは、文字列を適切に変換する必要があります。 アプリケーションでは、ユーザー インターフェイスでは、その日付を提示する場合は、ユーザーのカルチャで表示する必要があります。  
  
 ただし、アプリケーションは、中央のサーバーに、日付をアップロードする場合、は、可能性のあるさまざまな日付形式の間で混乱を避けるため、1 つの特定のカルチャに従って文字列を書式設定する必要があります。  
  
## <a name="culture-sensitive-functions"></a>カルチャに依存する関数  
 すべての Visual Basic の文字列変換関数 (を除き、`Str`と`Val`関数)、アプリケーションのカルチャ情報を使用して変換および比較がアプリケーションのカルチャに適切であるかどうかを確認ユーザー。  
  
 キーが正常に文字列変換関数を使用して別のカルチャ設定を持つコンピューターで実行されるアプリケーションでどの関数を使用して、特定のカルチャ設定と現在のカルチャ設定を使用するを理解することです。 アプリケーションのカルチャの設定は、既定では、設定から継承される、カルチャ、オペレーティング システムのことを確認します。 詳細については、次を参照してください。 <xref:Microsoft.VisualBasic.Strings.Asc%2A>、 <xref:Microsoft.VisualBasic.Strings.AscW%2A>、 <xref:Microsoft.VisualBasic.Strings.Chr%2A>、 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>、 <xref:Microsoft.VisualBasic.Strings.Format%2A>、 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>、 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>、および[型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)します。  
  
 `Str` (数値を文字列に変換) と`Val`文字列や数値の間で変換するときに (文字列数値からに変換) 関数がアプリケーションのカルチャ情報を使用しないでください。 代わりに、有効な 10 進区切り記号としてピリオド (.) のみを認識できるとします。 これらの関数のカルチャに対応して類似のものは次のとおりです。  
  
-   **現在のカルチャを使用する変換。** `CStr`と`Format`関数は、数値を文字列に変換し、`CDbl`と`CInt`関数では、文字列を数値に変換します。  
  
-   **特定のカルチャを使用する変換。** 各数値のオブジェクトには、 `ToString(IFormatProvider)` 、文字列に数値を変換するメソッドと`Parse(String, IFormatProvider)`文字列を数値に変換するメソッド。 たとえば、`Double`型を提供、<xref:System.Double.ToString%28System.IFormatProvider%29>と<xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>メソッド。  
  
 詳細については、次のトピックを参照してください。 <xref:Microsoft.VisualBasic.Conversion.Str%2A> および <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
  
## <a name="using-a-specific-culture"></a>特定のカルチャを使用します。  
 (文字列として書式設定) の日付を Web サービスに送信するアプリケーションを開発していることを想像してください。 この場合、アプリケーションでは、文字列変換のため、特定のカルチャを使用する必要があります。 その理由を示すためには、日付の使用の結果を検討してください。<xref:System.DateTime.ToString>メソッド。返しますが、アプリケーションでそのメソッドを使用して、2005 年 7 月 4 日の日付の書式設定するかどうかは"7/4/2005 12時 00分: 00 AM"、米国英語 (EN-US) カルチャの実行とは"04.07.2005 00時 00分: 00"ドイツ (DE-DE) のカルチャに実行するとします。  
  
 使用する必要がある、特定のカルチャの形式で文字列の変換を実行する必要がある場合、`CultureInfo`に組み込まれているクラス、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]します。 新規に作成することができます`CultureInfo`カルチャの名前を渡すことによって、特定のカルチャのオブジェクト、<xref:System.Globalization.CultureInfo.%23ctor%2A>コンス トラクター。 サポートされているカルチャの名前にある、<xref:System.Globalization.CultureInfo>ヘルプ ページのクラス。  
  
 インスタンスを取得する代わりに、*インバリアント カルチャ*から、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>プロパティ。 インバリアント カルチャが英語のカルチャに基づきますが、いくつか違いがあります。 たとえば、インバリアント カルチャでは、12 時間制ではなく、24 時間制を指定します。  
  
 日付をカルチャの文字列に変換するには、渡す、<xref:System.Globalization.CultureInfo>日オブジェクトのオブジェクト<xref:System.DateTime.ToString%28System.IFormatProvider%29>メソッド。 たとえば、次のコードが表示されます"07/04/2005 00時 00分: 00"アプリケーションのカルチャ設定に関係なく、します。  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
>  日付リテラルは常に英語のカルチャに従って解釈されます。  
  
## <a name="comparing-strings"></a>文字列の比較  
 これには、文字列比較が必要な 2 つの重要な状況があります。  
  
-   **ユーザーに表示するためのデータの並べ替え** 現在のカルチャに基づく文字列を適切に並べ替えるための操作を使用します。  
  
-   **アプリケーション内部の 2 つの文字列が (通常はセキュリティの目的で) 正確に一致するかどうかを決定します。** 現在のカルチャを無視して操作を使用します。  
  
 両方の種類の Visual Basic での比較を行うことができます<xref:Microsoft.VisualBasic.Strings.StrComp%2A>関数。 省略可能な指定`Compare`比較の種類を制御する引数:`Text`ほとんどの入力と出力の`Binary`完全一致を判断するためです。  
  
 `StrComp`関数は、並べ替え順序に基づいて 2 つの比較対象の文字列間のリレーションシップを示す整数を返します。 結果の正の値は、最初の文字列が 2 番目の文字列より大きいことを示します。 負の結果は、最初の文字列が小さく、および 0 は、文字列の間に等しいかどうかを示しますを示します。  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 使用することも、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]のパートナー、`StrComp`関数の場合、<xref:System.String.Compare%2A?displayProperty=nameWithType>メソッド。 これは、文字列の基本クラスの静的、オーバー ロードされたメソッドです。 次の例では、このメソッドを使用する方法を示しています。  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 その他のオーバー ロードを使用する比較を実行する方法をより細かく制御するには<xref:System.String.Compare%2A>メソッド。 <xref:System.String.Compare%2A?displayProperty=nameWithType>メソッドが使用できる、`comparisonType`引数を使用する比較の種類を指定します。  
  
|場合は値`comparisonType`引数|比較の種類|使用に適した状況|  
|---|---|---|  
|`Ordinal`|文字列のコンポーネントのバイト数に基づく比較。|この値を比較するときに使用します。 大文字の識別子、セキュリティ関連の設定、またはバイト数を正確に一致する必要があります、その他の非言語的な識別子。|  
|`OrdinalIgnoreCase`|文字列のコンポーネントのバイト数に基づく比較。<br /><br /> `OrdinalIgnoreCase` インバリアント カルチャ情報を使用して、2 つの文字が異なる場合にのみ大文字と小文字を決定します。|比較するときに、この値を使用します。 大文字の識別子、セキュリティ関連の設定、および Windows に格納されたデータ。|  
|`CurrentCulture` または `CurrentCultureIgnoreCase`|現在のカルチャで文字列の解釈に基づく比較。|比較するときに、これらの値を使用します。 ユーザー、ほとんどのユーザー入力、および言語的解釈を必要とするその他のデータに表示されるデータ。|  
|`InvariantCulture` または `InvariantCultureIgnoreCase`|インバリアント カルチャで文字列の解釈に基づく比較。<br /><br /> これは異なる、`Ordinal`と`OrdinalIgnoreCase`、インバリアント カルチャの許容範囲外の文字を等価のインバリアント文字として扱われるためです。|固定の並べ替え順序が必要なデータを保持するか、言語関連データの表示を比較するときにのみ、これらの値を使用します。|  
  
### <a name="security-considerations"></a>セキュリティの考慮事項  
 アプリケーションがセキュリティ上の決定の比較またはケース変更操作の結果に基づくかどうかは、操作を使用する必要があります、<xref:System.String.Compare%2A?displayProperty=nameWithType>メソッド、およびパス`Ordinal`または`OrdinalIgnoreCase`の`comparisonType`引数。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Globalization.CultureInfo>
- [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
