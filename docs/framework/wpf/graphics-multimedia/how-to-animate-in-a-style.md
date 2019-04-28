---
title: スタイル (WPF) でアニメーション化する方法
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 5fb18a2d927746c3437ec01d2a19327be373cae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789286"
---
# <a name="how-to-animate-in-a-style"></a>スタイル内でアニメーション化する方法

この例では、スタイル内でプロパティをアニメーション化する方法を示します。 スタイル内でアニメーション化するときに、スタイルが定義されているフレームワーク要素だけを直接ターゲットにできます。 Freezable オブジェクトを対象とする必要があります「ドット ダウン」スタイルの要素のプロパティから。

次の例では、複数のアニメーションのスタイル内で定義されているし、に適用される、<xref:System.Windows.Controls.Button>します。 部分的に透明とバックエンドを不透明なから消えてしまうと、ユーザーがマウス ボタン、もう一度、繰り返し。 ユーザーがボタンをマウスを移動すると完全に不透明になります。 ボタンをクリックすると、その背景色は白を再びオレンジから変更します。 <xref:System.Windows.Media.SolidColorBrush>描画に使用されるボタンを直接ターゲットにできない、ボタンからダウン求めたによりアクセスされる<xref:System.Windows.Controls.Control.Background%2A>プロパティ。

## <a name="example"></a>例

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

スタイル内でアニメーション化するときに、存在しないオブジェクトはターゲットにすることことに注意してください。 たとえば、自分のスタイルを使用して、<xref:System.Windows.Media.SolidColorBrush>ボタンの背景のプロパティの設定が、ある時点で、スタイルがオーバーライドされ、ボタンの背景が設定されている、<xref:System.Windows.Media.LinearGradientBrush>します。  アニメーション化しようとして、 <xref:System.Windows.Media.SolidColorBrush> ; 例外をスローしません、アニメーションはサイレント モードで失敗します。

構文を対象とするストーリー ボードの詳細については、次を参照してください。、[ストーリー ボードの概要](storyboards-overview.md)します。 アニメーションの詳細については、次を参照してください。、[アニメーションの概要](animation-overview.md)します。 スタイルの詳細については、次を参照してください。、[スタイルとテンプレート](../controls/styling-and-templating.md)します。
