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
ms.openlocfilehash: 57b73d3b80f0392b99aacfbfac4d8709f72d52e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186327"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML 構文
および などの<xref:System.Windows.Controls.Calendar><xref:System.Windows.Controls.DatePicker>一部のコントロールには、この型を<xref:System.DateTime>使用するプロパティがあります。 これらのコントロールに対する日付または時刻の初期値は、分離コードで実行時に指定するのが一般的です。ただし、日付または時刻の初期値を XAML で指定することもできます。 WPF XAML パーサーは、<xref:System.DateTime>組み込みの XAML テキスト構文を使用して値の解析を処理します。 このトピックでは、XAML テキスト構文の<xref:System.DateTime>詳細について説明します。  

<a name="where_datetime_xaml_syntax_is_used"></a>
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML 構文が使用される状況  
 日付は必ずしも XAML で設定する必要はありません。また、XAML で設定することが適切とは言えない場合もあります。 たとえば、このプロパティを<xref:System.DateTime.Now%2A?displayProperty=nameWithType>使用して実行時に日付を初期化したり、ユーザー入力に基づいて分離コード内の予定表の日付調整をすべて行うことができます。 ただし、日付<xref:System.Windows.Controls.Calendar><xref:System.Windows.Controls.DatePicker>をコントロール テンプレートにハードコーディングする場合があります。 これらの<xref:System.DateTime>シナリオでは、XAML 構文を使用する必要があります。  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML 構文はネイティブの動作  
 <xref:System.DateTime>は、CLR の基本クラス ライブラリで定義されているクラスです。 基本クラス ライブラリが CLR の他の部分とどのように関連するかにより、クラスに適用<xref:System.ComponentModel.TypeConverterAttribute>し、型コンバーターを使用して XAML からの文字列を処理し、ランタイム<xref:System.DateTime>オブジェクト モデルで文字列に変換することはできません。 変換動作を提供する `DateTimeConverter` クラスは存在しません。このトピックで説明する変換動作は、WPF XAML パーサーのネイティブな動作です。  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML 構文の書式指定文字列  
 フォーマット文字列を使用して、フォーマット<xref:System.DateTime>を指定できます。 書式指定文字列は、値を作成するときに使用できるテキスト構文を形式化します。 <xref:System.DateTime>既存の WPF コントロールの値は、通常は時間<xref:System.DateTime>コンポーネントではなく、日付コンポーネントのみを使用します。  
  
 XAML で<xref:System.DateTime>を指定する場合は、任意の書式指定文字列を同じ意味で使用できます。  
  
 また、このトピックで特に示されていない形式および書式指定文字列も使用できます。 技術的には、WPF XAML<xref:System.DateTime>パーサーによって指定され解析される任意の値の XAML は、 への<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>内部呼び出しを使用するため、XAML 入力に受<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>け入れられる任意の文字列を使用できます。 詳細については、<xref:System.DateTime.Parse%2A?displayProperty=nameWithType> を参照してください。  
  
> [!IMPORTANT]
> DateTime XAML 構文では`en-us`、常<xref:System.Globalization.CultureInfo>にそのネイティブ変換の として使用されます。 XAML の属性レベル<xref:System.Windows.FrameworkElement.Language%2A>の型`xml:lang`変換は、そのコンテキストなしで動作するため、XAML の値または値の影響を受けません。 日や月を表示する順序などにはカルチャによる違いがあるため、ここで示した書式指定文字列は補完しないでください。 ここで示した書式指定文字列は、その他のカルチャ設定に関係なく、XAML を解析する場合に適しています。  
  
 以下のセクションでは、一般的な<xref:System.DateTime>書式指定文字列について説明します。  
  
### <a name="short-date-pattern-d"></a>短い形式の日付パターン ("d")  
 次に、XAML の短い日付<xref:System.DateTime>形式を示します。  
  
 `M/d/YYYY`  
  
 これは、WPF コントロールでの一般的な使用法で、必要なすべての情報を指定するための最も簡単な形式です。タイム ゾーン オフセットと時刻要素を誤って指定した場合でも影響を受けないため、他の形式ではなく、この形式の使用をお勧めします。  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します。  
  
 `3/1/2010`  
  
 詳細については、<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> を参照してください。  
  
### <a name="sortable-datetime-pattern-s"></a>並べ替えできる DateTime のパターン ("s")  
 XAML での並べ<xref:System.DateTime>替え可能なパターンを次に示します。  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します (時刻要素はすべて 0 として入力されます)。  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 パターン ("r")  
 RFC1123 パターンの利点は、カルチャに依存しないために、RFC1123 パターンが使用されている他の日付ジェネレーターから入力された文字列を使用できることです。 次に、XAML の RFC1123<xref:System.DateTime>パターンを示します。  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します (時刻要素はすべて 0 として入力されます)。  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>その他の形式とパターン  
 前述のように、 in <xref:System.DateTime> XAML は、 の入力として受け入れられる任意<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>の文字列として指定できます。 これには、他の形式形式 (たとえば<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) や、特定<xref:System.Globalization.DateTimeFormatInfo>の形式として形式化されていない形式が含まれます。 たとえば、フォーム`YYYY/mm/dd`は の入力として受け<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>入れられます。 このトピックでは、使用可能な形式の一部を説明します。標準的な使用手順としては、短い形式の日付パターンをお勧めします。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
