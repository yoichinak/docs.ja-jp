---
title: プレビュー イベント
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 75165df94aa8b508ef85cf970933efb98b9d62ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772880"
---
# <a name="preview-events"></a>プレビュー イベント
プレビュー イベント、トンネル イベントとも呼ばれますにはルーティング イベントがあるイベントを発生し、イベント データのソースとして報告された要素に対するアプリケーションのルートからルートの方向が送信されます。 すべてのイベント シナリオがサポートまたはプレビュー イベント; が必要です。このトピックでは、カスタム コンポーネントまたはクラスでプレビュー イベントを作成する可能性がありますが、適切なである場合、プレビュー イベントが存在、アプリケーションまたはコンポーネントを処理する方法、それらの状況について説明します。  
  
## <a name="preview-events-and-input"></a>プレビュー イベントと入力  
 イベントは一般に、注意するプレビューを処理するときに、イベントをマークすることでイベント処理データ。 以外の任意の要素でプレビュー イベントを処理すること (イベント データのソースとして報告される要素) を発生させた要素は、要素外の発生するイベントを処理する機会を提供しない効果があります。 場合があります内でのコントロールの複合リレーションシップに問題の要素が存在しない場合に特に、目的の結果になります。  
  
 入力イベントを具体的には、プレビュー イベントを共有もイベント データ インスタンス、同等のバブル イベント。 プレビュー イベントのクラス ハンドラーを使用して、入力イベントを処理済みのマークする場合、バブル入力イベントのクラス ハンドラーは呼び出されません。 または、プレビュー イベントのインスタンス ハンドラーにイベントを処理済みのマークを使用する場合、バブル イベントのハンドラーは通常呼び出されません。 クラス ハンドラーやインスタンス ハンドラーを登録またはアタッチする手法は通常使用されませんが、イベントが処理された、マークされている場合でも呼び出されるオプション。  
  
 クラスの処理とプレビュー イベントに関連付ける方法の詳細については、次を参照してください。[ルーティング イベントの処理済み、およびクラス処理としてのマーキング](marking-routed-events-as-handled-and-class-handling.md)します。  
  
### <a name="working-around-event-suppression-by-controls"></a>コントロールによるイベント抑制の回避  
 プレビュー イベントが頻繁に使用されている 1 つのシナリオが、複合コントロールの入力イベントを処理します。 場合によっては、コントロールの作成者より多くの情報をより具体的な動作を表すコンポーネント定義のイベントを置換するには、おそらくそのコントロールでは、送信元から特定のイベントを抑制します。 たとえば、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>を抑制します<xref:System.Windows.UIElement.MouseLeftButtonDown>と<xref:System.Windows.UIElement.MouseRightButtonDown>によって生成されるイベントのバブリング、<xref:System.Windows.Controls.Button>またはマウスをキャプチャして発生を優先してその複合要素を<xref:System.Windows.Controls.Primitives.ButtonBase.Click>によって常に発生するイベントを<xref:System.Windows.Controls.Button>自体。 イベントとそのデータ、ルートでは、引き続きだ、 <xref:System.Windows.Controls.Button> 、イベント データをマーク<xref:System.Windows.RoutedEventArgs.Handled%2A>で動作する必要がありますが、個別に指定したイベントのハンドラーにのみ、`handledEventsToo`ケースが呼び出されます。  代わりをコードでハンドラーをアタッチする場合は、アプリケーションのルートに近い方には、その他の要素もコントロールで抑制されたイベントを処理すること、`handledEventsToo`として指定された`true`します。 プレビューと同等の入力イベントを処理するルーティングの方向を変更する単純な手法は、多くの場合。 たとえば、コントロールを抑制する場合<xref:System.Windows.UIElement.MouseLeftButtonDown>、ハンドラーを添付するをお試しください<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>代わりにします。 この手法だけが、基本要素の入力イベントなど<xref:System.Windows.UIElement.MouseLeftButtonDown>します。 これらの入力イベントは、トンネル/バブルのペアを使用して、両方のイベントを発生させるし、イベント データを共有します。  
  
 これらの手法が、副作用または制限事項のいずれか。 プレビュー イベントの処理の副作用は、バブル イベントを処理するハンドラーが無効にイベントをその時点で処理をそのため、制限がある通常いない処理、Previ にまだ残っているイベントをマークすることをお勧め新しいルートの一部です。 制限、`handledEventsToo`手法は指定できません、`handledEventsToo`ハンドラー[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を属性としてする必要がありますに登録するイベント ハンドラーのコード ハンドラーがアタッチされる要素へのオブジェクト参照を取得した後。  
  
## <a name="see-also"></a>関連項目

- [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)
- [ルーティング イベントの概要](routed-events-overview.md)
