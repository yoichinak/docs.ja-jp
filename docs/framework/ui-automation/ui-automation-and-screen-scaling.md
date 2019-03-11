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
ms.openlocfilehash: 4b2988314afbe501623fd050a989876842f68601
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674537"
---
# <a name="ui-automation-and-screen-scaling"></a>UI オートメーションおよび画面の拡大縮小
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] では、ユーザーが [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] 設定を変更して、画面上のほとんどの [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 要素を拡大表示できます。 この機能は長い間、 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]で有効でしたが、以前のバージョンでは、アプリケーションによって拡大縮小を実装しなければなりませんでした。 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]では、独自の拡大縮小処理を行わないアプリケーションのすべてについて、デスクトップ ウィンドウ マネージャーが既定の拡大縮小を行います。 UI オートメーション クライアント アプリケーションでは、この機能を考慮に入れる必要があります。  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista での拡大縮小  
 既定の [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定は 96 です。つまり、幅または高さの概念上の 1 インチが 96 ピクセルで占められます。 「インチ」の正確な寸法は、モニターのサイズと物理的な解像度によって異なります。 たとえば、幅 12 インチで水平方向の解像度 1280 ピクセルのモニターでは、96 ピクセルの水平線は 1 インチの約 9/10 の長さになります。  
  
 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定を変更することは、画面の解像度を変更することと同じではありません。 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] の拡大縮小では、画面上の物理的ピクセル数はそのまま変わりません。 拡大縮小が適用されるのは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素のサイズと位置です。 拡大縮小しないよう明示的に指定されていないデスクトップとアプリケーションに対し、デスクトップ ウィンドウ マネージャー (DWM) はこの拡大縮小を自動的に実行できます。  
  
 実際には、ユーザーがスケール ファクターを 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]に設定すると、画面上の垂直または水平方向のインチが 25% 拡大されます。 すべての寸法は、それに応じて拡大されます。 画面の左上隅からのアプリケーション ウィンドウのオフセットは、25% 増加します。 アプリケーションの拡大縮小が有効であり、アプリケーションが [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]対応でない場合、ウィンドウのサイズが同じ比率で大きくなります。ウィンドウに含まれるすべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素のオフセットとサイズも同様です。  
  
> [!NOTE]
>  既定では、ユーザーが[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]を 120 に設定した場合、DWM は [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 非対応のアプリケーションに対して拡大縮小を実行しませんが、 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] が 144 以上のカスタム値に設定されている場合には拡大縮小を実行します。 ただし、この既定の動作は、ユーザーがオーバーライドできます。  
  
 画面の拡大縮小は、画面座標に何らかの関わりを持つアプリケーションに新しい課題をもたらします。 現在、画面には物理座標と論理座標という 2 つの座標系が含まれています。 あるポイントの物理座標は、原点の左上からの実際のオフセット (ピクセル数) です。 論理座標は、ピクセル自体が拡大縮小された場合のオフセットです。  
  
 たとえば、ダイアログ ボックスを設計し、座標 (100, 48) にボタンを配置するとします。 このダイアログ ボックスが既定の 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]で表示される場合、ボタンは物理座標 (100, 48) に位置します。 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]の場合は、物理座標 (125, 60) に位置します。 論理座標は任意で同じ[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]設定。(100, 48).  
  
 論理座標は、 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] の設定に関係なく、オペレーティング システムとアプリケーションの動作を一貫性のあるものとするので重要です。 たとえば、 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> は通常、論理座標を返します。 カーソルをダイアログ ボックス内の要素に移動すると、 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] の設定に関係なく、同じ座標が返されます。 (100, 100) にコントロールを描画する場合、そのコントロールはこの論理座標に描画され、 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] の設定に関係なく、同じ相対位置を占めることになります。  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>UI オートメーション クライアントにおける拡大縮小  
  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] は論理座標を使用しません。 次のメソッドとプロパティが返す、あるいはパラメーターとして受け取るのは、物理座標です。  
  
-   <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ではない環境で実行されている UI オートメーション クライアント アプリケーションは、既定では、これらのメソッドとプロパティから正しい結果を取得できません。 たとえば、カーソルの位置は論理座標で表されるため、クライアントはそのカーソルの位置にある要素を取得するために、これらの座標をそのまま <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> に渡すことができません。 さらに、アプリケーションはクライアント領域外にウィンドウを正しく配置することもできません。  
  
 解決方法は 2 つの部分で構成されます。  
  
1.  まず、クライアント アプリケーションを [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]対応にします。 それには、起動時に [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 関数 `SetProcessDPIAware` を呼び出します。 マネージド コードで、次の宣言によりこの関数を使用できるようになります。  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     この関数は、プロセス全体を dpi 対応では、プロセスに属するすべての windows がスケーリングされたいないことを意味します。 [蛍光ペン サンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)、たとえば、強調表示の四角形を構成する 4 つのウィンドウは、UI オートメーション、論理座標ではないから取得した物理座標にあります。 サンプルが dpi 対応でない場合、強調表示はデスクトップであるため、96 dpi ではない環境では正しく配置論理座標で描画します。  
  
2.  カーソルの座標を取得するには、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 関数 `GetPhysicalCursorPos`を呼び出します。 次の例に、この関数を宣言して使用する方法を示します。  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>は使用しないでください。 拡大縮小される環境において、クライアント ウィンドウ外でのこのプロパティの動作は定義されていません。  
  
 アプリケーションが [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]非対応のアプリケーションと直接プロセス間通信を行う場合は、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 関数 `PhysicalToLogicalPoint` および `LogicalToPhysicalPoint`を使用して、論理座標と物理座標を互いに変換できます。  
  
## <a name="see-also"></a>関連項目
- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
