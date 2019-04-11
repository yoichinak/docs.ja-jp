---
title: DateTime XAML 構文
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: d7fe5f15f79ab068e88c3fb6f7b7cac0986aa636
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146498"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML 構文
などのいくつかのコントロール<xref:System.Windows.Controls.Calendar>と<xref:System.Windows.Controls.DatePicker>を使用したプロパティ、<xref:System.DateTime>型。 これらのコントロールに対する日付または時刻の初期値は、分離コードで実行時に指定するのが一般的です。ただし、日付または時刻の初期値を XAML で指定することもできます。 WPF XAML パーサーの処理の解析<xref:System.DateTime>組み込み XAML テキスト構文を使用して値します。 このトピックの詳細を記述する、 <xref:System.DateTime> XAML テキスト構文。  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML 構文が使用される状況  
 日付は必ずしも XAML で設定する必要はありません。また、XAML で設定することが適切とは言えない場合もあります。 たとえば、使用する、<xref:System.DateTime.Now%2A?displayProperty=nameWithType>プロパティで、実行時の日付を初期化するためには、ユーザー入力に基づいて、コード分離の予定表の日付のすべての調整を行うことができます。 ただし、シナリオにハードコードされた日付にすることがありますがある、<xref:System.Windows.Controls.Calendar>と<xref:System.Windows.Controls.DatePicker>コントロール テンプレートにします。 <xref:System.DateTime> XAML 構文は、これらのシナリオのために使用する必要があります。  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML 構文はネイティブの動作  
 <xref:System.DateTime> CLR の基本クラス ライブラリで定義されているクラスです。 ための基本クラス ライブラリは、CLR の残りの部分に関連付ける方法、そのことはできませんを適用する<xref:System.ComponentModel.TypeConverterAttribute>クラスを使用して XAML から文字列を処理し、それらを変換する型コンバーターを<xref:System.DateTime>実行時のオブジェクト モデルです。 変換動作を提供する `DateTimeConverter` クラスは存在しません。このトピックで説明する変換動作は、WPF XAML パーサーのネイティブな動作です。  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML 構文の書式指定文字列  
 形式を指定することができます、<xref:System.DateTime>を書式文字列。 書式指定文字列は、値を作成するときに使用できるテキスト構文を形式化します。 <xref:System.DateTime> 値は既存の WPF コントロールの日付要素が一般にのみ使用<xref:System.DateTime>と時刻のコンポーネントではありません。  
  
 指定するときに、 <xref:System.DateTime> XAML に置き換えて使用できます、書式指定文字列のいずれか。  
  
 また、このトピックで特に示されていない形式および書式指定文字列も使用できます。 いずれかの XAML では技術的には、<xref:System.DateTime>指定され、WPF XAML パーサーによって解析される値への内部呼び出しを使用して<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>で受け入れられる任意の文字列を使用するため<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>XAML 入力します。 詳細については、「 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 」を参照してください。  
  
> [!IMPORTANT]
>  DateTime XAML 構文を使用して常に`en-us`として、<xref:System.Globalization.CultureInfo>ネイティブ変換用。 これによって受けません<xref:System.Windows.FrameworkElement.Language%2A>値または`xml:lang`XAML 属性レベルの型変換がそのコンテキストを使用せずに動作するため、XAML 内の値します。 日や月を表示する順序などにはカルチャによる違いがあるため、ここで示した書式指定文字列は補完しないでください。 ここで示した書式指定文字列は、その他のカルチャ設定に関係なく、XAML を解析する場合に適しています。  
  
 以下のセクションでは、共通の一部について説明します<xref:System.DateTime>書式指定文字列。  
  
### <a name="short-date-pattern-d"></a>短い形式の日付パターン ("d")  
 短い日付形式を次に示します、 <xref:System.DateTime> XAML で。  
  
 `M/d/YYYY`  
  
 これは、WPF コントロールでの一般的な使用法で、必要なすべての情報を指定するための最も簡単な形式です。タイム ゾーン オフセットと時刻要素を誤って指定した場合でも影響を受けないため、他の形式ではなく、この形式の使用をお勧めします。  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します。  
  
 `3/1/2010`  
  
 詳細については、「 <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> 」を参照してください。  
  
### <a name="sortable-datetime-pattern-s"></a>並べ替えできる DateTime のパターン ("s")  
 次の表示、並べ替え可能な<xref:System.DateTime>XAML 内のパターン。  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します (時刻要素はすべて 0 として入力されます)。  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 パターン ("r")  
 RFC1123 パターンの利点は、カルチャに依存しないために、RFC1123 パターンが使用されている他の日付ジェネレーターから入力された文字列を使用できることです。 次に示します、RFC1123 <xref:System.DateTime> XAML 内のパターン。  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します (時刻要素はすべて 0 として入力されます)。  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>その他の形式とパターン  
 以前は、説明したように、 <xref:System.DateTime> XAML では、許容される任意の文字列として指定できますの入力として<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>します。 その他の形式化された形式が含まれます (たとえば<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>)、および特定として形式化されていない形式<xref:System.Globalization.DateTimeFormatInfo>フォーム。 たとえば、フォーム`YYYY/mm/dd`が許容される入力として<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>します。 このトピックでは、使用可能な形式の一部を説明します。標準的な使用手順としては、短い形式の日付パターンをお勧めします。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](xaml-overview-wpf.md)
