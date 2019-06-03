---
ms.openlocfilehash: 335647f899c79eff22e313fa40b2e2a73e7cfff0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379593"
---
### <a name="wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF による Expressions.Literal\<T> DateTimes のシリアル化の方法が変わった (カスタム XAML パーサーが機能しなくなる)

|   |   |
|---|---|
|説明|関連する <xref:System.Windows.Markup.ValueSerializer> オブジェクトは、Second コンポーネントと <xref:System.DateTime.Millisecond?displayProperty=name> コンポーネントが非ゼロで (<xref:System.DateTime?displayProperty=name> 値の場合)、<xref:System.DateTime.Kind> プロパティが Unspecified ではない <xref:System.DateTime?displayProperty=name> オブジェクトまたは <xref:System.DateTimeOffset?displayProperty=name> オブジェクトを文字列ではなくプロパティ要素構文に変換します。 この変更により、<xref:System.DateTime?displayProperty=name> 値と <xref:System.DateTimeOffset?displayProperty=name> 値を往復させることができるようになります。 入力 XAML が属性構文であると想定するカスタム XAML パーサーは正しく機能しません。|
|提案される解決策|この変更により、<xref:System.DateTime?displayProperty=name> 値と <xref:System.DateTimeOffset?displayProperty=name> 値を往復させることができるようになります。 入力 XAML が属性構文であると想定するカスタム XAML パーサーは正しく機能しません。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
