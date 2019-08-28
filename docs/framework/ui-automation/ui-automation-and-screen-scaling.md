---
title: UI オートメーションおよび画面の拡大縮小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: 35b46d2030ee887eb98618fbed127097cec1f0c5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044193"
---
# <a name="ui-automation-and-screen-scaling"></a>UI オートメーションおよび画面の拡大縮小
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]画面上のほとんど[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]の要素が大きく表示されるように、ユーザーがドット/インチ (dpi) 設定を変更できるようにします。 この機能は長い間、 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]で有効でしたが、以前のバージョンでは、アプリケーションによって拡大縮小を実装しなければなりませんでした。 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]では、独自の拡大縮小処理を行わないアプリケーションのすべてについて、デスクトップ ウィンドウ マネージャーが既定の拡大縮小を行います。 UI オートメーション クライアント アプリケーションでは、この機能を考慮に入れる必要があります。  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista での拡大縮小  
 既定の dpi 設定は96です。これは、96ピクセルが1概念的なインチの幅または高さを占めていることを意味します。 「インチ」の正確な寸法は、モニターのサイズと物理的な解像度によって異なります。 たとえば、幅 12 インチで水平方向の解像度 1280 ピクセルのモニターでは、96 ピクセルの水平線は 1 インチの約 9/10 の長さになります。  
  
 Dpi 設定の変更は、画面の解像度の変更と同じではありません。 Dpi スケーリングでは、画面上の物理ピクセルの数は変わりません。 拡大縮小が適用されるのは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素のサイズと位置です。 拡大縮小しないよう明示的に指定されていないデスクトップとアプリケーションに対し、デスクトップ ウィンドウ マネージャー (DWM) はこの拡大縮小を自動的に実行できます。  
  
 実際には、ユーザーがスケールファクターを 120 dpi に設定すると、画面上の垂直方向または水平方向のインチが 25% 大きくなります。 すべての寸法は、それに応じて拡大されます。 画面の左上隅からのアプリケーション ウィンドウのオフセットは、25% 増加します。 アプリケーションのスケーリングが有効になっていて、アプリケーションが dpi 対応でない場合、ウィンドウのサイズは、含まれるすべて[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の要素のオフセットとサイズと共に、同じ比率で増加します。  
  
> [!NOTE]
> 既定では、DWM は dpi が120に設定されている場合は dpi 非対応アプリケーションのスケーリングを実行しませんが、dpi が144以上のカスタム値に設定されている場合は、この動作を実行します。 ただし、この既定の動作は、ユーザーがオーバーライドできます。  
  
 画面の拡大縮小は、画面座標に何らかの関わりを持つアプリケーションに新しい課題をもたらします。 現在、画面には物理座標と論理座標という 2 つの座標系が含まれています。 あるポイントの物理座標は、原点の左上からの実際のオフセット (ピクセル数) です。 論理座標は、ピクセル自体が拡大縮小された場合のオフセットです。  
  
 たとえば、ダイアログ ボックスを設計し、座標 (100, 48) にボタンを配置するとします。 このダイアログボックスが既定の 96 dpi で表示されている場合、ボタンはの物理座標 (100、48) にあります。 120 dpi では、(125、60) の物理座標に配置されます。 ただし、論理座標はどの dpi 設定でも同じです。(100、48)。  
  
 論理座標は、dpi 設定に関係なく、オペレーティングシステムとアプリケーションの動作が一貫しているため、重要です。 たとえば、 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> は通常、論理座標を返します。 ダイアログボックス内の要素の上にカーソルを移動すると、dpi 設定に関係なく同じ座標が返されます。 (100, 100) にコントロールを描画すると、それらの論理座標に描画され、すべての dpi 設定で同じ相対位置が使用されます。  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>UI オートメーション クライアントにおける拡大縮小  
 API [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]は論理座標を使用しません。 次のメソッドとプロパティが返す、あるいはパラメーターとして受け取るのは、物理座標です。  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 既定では、96 dpi 以外の環境で実行されている UI オートメーションクライアントアプリケーションは、これらのメソッドとプロパティから正しい結果を得ることができません。 たとえば、カーソルの位置は論理座標で表されるため、クライアントはそのカーソルの位置にある要素を取得するために、これらの座標をそのまま <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> に渡すことができません。 さらに、アプリケーションはクライアント領域外にウィンドウを正しく配置することもできません。  
  
 解決方法は 2 つの部分で構成されます。  
  
1. まず、クライアントアプリケーションを dpi 対応にします。 それには、起動時に [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 関数 `SetProcessDPIAware` を呼び出します。 マネージド コードで、次の宣言によりこの関数を使用できるようになります。  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     この関数は、プロセス全体を dpi 対応にします。つまり、プロセスに属するすべてのウィンドウはスケーリングされません。 [蛍光ペンのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)では、強調表示の四角形を構成する4つのウィンドウは、論理座標ではなく、UI オートメーションから取得した物理座標に配置されます。 サンプルが dpi に対応していない場合、強調表示はデスクトップ上の論理座標に描画されます。これにより、96 dpi 以外の環境での配置が不適切になります。  
  
2. カーソルの座標を取得するには、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 関数 `GetPhysicalCursorPos`を呼び出します。 次の例に、この関数を宣言して使用する方法を示します。  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>は使用しないでください。 拡大縮小される環境において、クライアント ウィンドウ外でのこのプロパティの動作は定義されていません。  
  
 アプリケーションが非 dpi 対応アプリケーションとの間で直接通信を行う場合は、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]関数`PhysicalToLogicalPoint`と`LogicalToPhysicalPoint`を使用して論理座標と物理座標を変換することができます。  
  
## <a name="see-also"></a>関連項目

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
