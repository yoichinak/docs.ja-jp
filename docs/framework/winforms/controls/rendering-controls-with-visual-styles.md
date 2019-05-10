---
title: visual スタイルが使用されているコントロールのレンダリング
ms.date: 03/30/2017
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
ms.openlocfilehash: b97ce0e4ce32e272ff884240b566c1c1c0e0d271
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614660"
---
# <a name="rendering-controls-with-visual-styles"></a>visual スタイルが使用されているコントロールのレンダリング
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] は、視覚スタイルをサポートするオペレーティング システムでの、それらを使用したコントロールと他の Windows ユーザー インターフェイス (UI) 要素のレンダリングをサポートします。 このトピックでは、オペレーティング システムの現在の視覚スタイルを使用したコントロールと他の UI 要素のレンダリングに関して [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] でのいくつかのサポート レベルについて説明します。  
  
## <a name="rendering-classes-for-common-controls"></a>一般的なコントロールのクラスをレンダリングする  
 コントロールのレンダリングとは、コントロールのユーザー インターフェイスを描画することを意味します。 <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、いくつかの一般的な Windows フォーム コントロールをレンダリングするための <xref:System.Windows.Forms.ControlPaint> クラスを提供します。 ただし、このクラスは従来の Windows スタイルでコントロールを描画するため、視覚スタイルが有効になったアプリケーションでカスタム コントロールを描画する際の一貫した UI エクスペリエンスの維持が困難になる可能性があります。  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] に含まれる <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間のクラスは、視覚スタイルを使用して一般的なコントロールのパーツと状態をレンダリングします。 これらの各クラスに含まれる `static` メソッドにより、オペレーティング システムの現在の視覚スタイルを使用して、特定の状態のコントロールまたはコントロールのパーツを描画します。  
  
 これらのクラスの一部は、視覚スタイルが使用可能かどうかに関係なく関連するコントロールを描画するように設計されています。 視覚スタイルが有効になっている場合、クラス メンバーは視覚スタイルを使用して関連するコントロールを描画します。視覚スタイルが無効になっている場合、クラス メンバーは、従来の Windows スタイルでコントロールを描画します。 次のようなクラスがこれに含まれます。  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 他のクラスは、視覚スタイルが使用可能な場合にのみ関連するコントロールを描画することができ、視覚スタイルが無効になっている場合、それらのメンバーは例外をスローします。 次のようなクラスがこれに含まれます。  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 コントロールを描画するためにこれらのクラスの使用に関する詳細については、次を参照してください。[方法。コントロールの描画クラスを使用して、](how-to-use-a-control-rendering-class.md)します。  
  
## <a name="visual-style-element-and-rendering-classes"></a>視覚スタイル要素とレンダリング クラス  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> 名前空間に含まれるクラスを使用して、視覚スタイルによってサポートされる任意のコントロールまたは UI 要素を描画したり、それらに関する情報を取得したりすることができます。 サポートされるコントロールには、 <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間のレンダリング クラスを使用する一般的なコントロール (前のセクションを参照してください)、およびタブ コントロールや rebar コントロールなどの他のコントロールが含まれます。 他のサポートされる UI 要素には、 **[スタート]** メニュー、タスクバー、ウィンドウの非クライアント領域のパーツなどがあります。  
  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> 名前空間の主要なクラスは <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> と <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>です。 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> は、視覚スタイルによってサポートされる任意のコントロールまたはユーザー インターフェイス要素を識別するための基盤クラスです。 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 自体に加えて、 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> 名前空間には、視覚スタイルによってサポートされるコントロール、コントロール パーツ、その他の UI 要素のすべての状態の <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> を返す `static` プロパティを持つ <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> の多くの入れ子になったクラスが含まれています。  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> は、オペレーティング システムの現在の視覚スタイルによって定義される各 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> を描画したり、それらに関する情報を取得したりするメソッドを提供します。 取得可能な要素に関する情報には、既定のサイズ、背景の種類、色の定義などが含まれます。 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> は、Windows プラットフォーム SDK の Windows シェル部分からの視覚スタイル (UxTheme) API の機能をラップします。 詳細については、次を参照してください。 [Visual スタイルを有効にする](/windows/desktop/controls/cookbook-overview)します。  
  
 使用しての詳細については<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>と<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>を参照してください[方法。Visual スタイル要素を描画](how-to-render-a-visual-style-element.md)します。  
  
## <a name="enabling-visual-styles"></a>視覚スタイルを有効にする  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] バージョン 1.0 用に作成されたアプリケーションの視覚スタイルを有効にするには、プログラマーが、ComCtl32.dll バージョン 6 以降をコントロールの描画に使用することを指定するアプリケーション マニフェストを含める必要があります。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] バージョン 1.1 以降を使用してビルドされたアプリケーションは、 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> クラスの <xref:System.Windows.Forms.Application> メソッドを使用できます。  
  
## <a name="checking-for-visual-styles-support"></a>視覚スタイルのサポートの確認  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> クラスの <xref:System.Windows.Forms.Application> プロパティは、現在のアプリケーションが視覚スタイルを使用してコントロールを描画しているかどうかを示します。 カスタム コントロールを描画するときには、 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> の値を確認して、コントロールのレンダリングに視覚スタイルを使用する必要があるかどうかを判断できます。 次の表に、 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> が `true`を返すために満たす必要がある 4 つの条件を示します。  
  
|条件|メモ|  
|---------------|-----------|  
|オペレーティング システム視覚スタイルをサポートしている。|この条件を個別に確認するには、 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> クラスの <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> プロパティを使用します。|  
|ユーザーがオペレーティング システムで視覚スタイルを有効にしている。|この条件を個別に確認するには、 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> クラスの <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> プロパティを使用します。|  
|アプリケーションで視覚スタイルが有効になっている。|アプリケーションで視覚スタイルを有効にするには、 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> メソッドを呼び出すか、ComCtl32.dll バージョン 6 以降をコントロールの描画に使用することを指定するアプリケーション マニフェストを使用します。|  
|アプリケーション ウィンドウのクライアント領域を描画するために視覚スタイルが使用されている。|この条件を個別に確認するには、 <xref:System.Windows.Forms.Application.VisualStyleState%2A> クラスの <xref:System.Windows.Forms.Application> プロパティを使用し、その値が <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> または <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>になっていることを確認します。|  
  
 ユーザーが視覚スタイルの有効と無効を切り替えたり、1 つの視覚スタイルから別の視覚スタイルに切り替えたりしたときに、それを確認するには、 <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> または <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> イベントのハンドラーの <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> 値を確認します。  
  
> [!IMPORTANT]
>  ユーザーが視覚スタイルを有効にしたり切り替えたりしたときに、 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> を使用してコントロールまたは UI 要素をレンダリングする場合は、 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> イベントではなく <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> イベントを処理するときにこの処理を実行してください。 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> を処理するときに <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>クラスを使用した場合は、例外がスローされます。  
  
## <a name="see-also"></a>関連項目

- [コントロールのカスタム描画およびレンダリング](custom-control-painting-and-rendering.md)
