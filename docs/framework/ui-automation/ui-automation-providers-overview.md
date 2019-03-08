---
title: UI オートメーション プロバイダーの概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: d1209580070c628b8756d01e940a956060223d16
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680149"
---
# <a name="ui-automation-providers-overview"></a>UI オートメーション プロバイダーの概要
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 UI オートメーション プロバイダーを使用すれば、コントロールで UI オートメーション クライアント アプリケーションと通信することができます。 一般に、各コントロールまたは [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 内のその他の要素はプロバイダーによって表現されます。 プロバイダーは、要素に関する情報を公開し、必要に応じて、クライアント アプリケーションがコントロールと対話できるようにするコントロール パターンを実装します。  
  
 通常、クライアント アプリケーションはプロバイダーと直接連動する必要はありません。 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]、または [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] フレームワークを使用するアプリケーション内の標準コントロールのほとんどが自動的に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] システムに公開されます。 カスタム コントロールを実装するアプリケーションがそれらのコントロール用の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロバイダーを実装することもできます。クライアント アプリケーションがそれらにアクセスするために特別な手順を実行する必要はありません。  
  
 このトピックでは、コントロールの開発者が [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] と [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] のウィンドウのコントロール専用に [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] プロバイダーを実装する方法について説明します。  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>プロバイダーの種類  
 UI オートメーション プロバイダーは、クライアント側プロバイダーとサーバー側プロバイダーの 2 つのカテゴリに分類されます。  
  
### <a name="client-side-providers"></a>クライアント側プロバイダー  
 クライアント側プロバイダーは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]をサポートしていないか部分的にサポートしているアプリケーションと通信する UI オートメーション クライアントによって実装されます。 クライアント側プロバイダーは、通常サーバーと通信プロセス境界を越えて Windows メッセージを送受信することで。  
  
 ため、UI オートメーション プロバイダーでのコントロールの[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]、Windows フォーム、または[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]アプリケーションがオペレーティング システムの一部として提供される、クライアント アプリケーションは、独自のプロバイダーを実装することはほとんどありませんが、この概要では扱いませんさらにします。  
  
### <a name="server-side-providers"></a>サーバー側プロバイダー  
 サーバー側プロバイダーは、カスタム コントロールや UI フレームワークに基づく以外のアプリケーションによって、実装[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]、Windows フォーム、または[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]します。  
  
 また、サーバー側プロバイダーは、サーバーからクライアントに要求するインターフェイスを [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コア システムに公開することにより、プロセス境界を越えてクライアント アプリケーションと通信します。  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>UI オートメーション プロバイダーの概念  
 ここでは、UI オートメーション プロバイダーを実装するために理解しておく必要があるいくつかの重要な概念について簡単に説明します。  
  
### <a name="elements"></a>Elements  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素は、UI オートメーション クライアントからアクセス可能な [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] の一部です。 例として、アプリケーション ウィンドウ、ペイン、ボタン、ツールヒント、リスト ボックス、およびリスト項目が含まれています。  
  
### <a name="navigation"></a>ナビゲーション  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーとしてクライアントに公開されます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、要素間を移動することによって、ツリーを構成します。 ナビゲーションは、親、兄弟、または子を指す要素ごとに、プロバイダーによって有効にされます。  
  
 クライアントの表示の詳細については、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーを参照してください[UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)します。  
  
### <a name="views"></a>Views  
 次の表に示すように、クライアントは 3 つのプリンシパル ビューで [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーを表示できます。  
  
|||  
|-|-|  
|列ビュー|すべての要素が含まれます。|  
|コントロール ビュー|コントロールである要素が含まれます。|  
|コンテンツ ビュー|コンテンツである要素が含まれます。|  
  
 クライアント ビューの詳細については、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーを参照してください[UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)します。  
  
 コンテンツ要素またはコントロール要素としての要素の定義はプロバイダー実装で行う必要があります。 コントロール要素はコンテンツ要素であることもないこともありますが、コンテンツ要素はすべてコントロール要素です。  
  
### <a name="frameworks"></a>フレームワーク  
 フレームワークは、画面のある領域で子コントロール、ヒット テスト、およびレンダリングを管理するコンポーネントです。 たとえば、HWND とも呼ばれる [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ウィンドウは、メニュー バー、ステータス バー、ボタンなどの [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素が複数含まれるフレームワークとして機能することができます。  
  
 リスト ボックスやツリー ビューなどの[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] コンテナー コントロールは、子項目をレンダリングしたり、それらに対してヒット テストを実行したりするための独自のコードが含まれているため、フレームワークと見なされます。 これに対して、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] リスト ボックスは、包含する [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ウィンドウによってレンダリングやヒット テストが処理されるため、フレームワークではありません。  
  
 アプリケーション内の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] はさまざまなフレームワークで構成することができます。 たとえば、HWND アプリケーション ウィンドウには、HWND 内のコンボ ボックスなどのコンポーネントを含む [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] を含めることができます。  
  
### <a name="fragments"></a>フラグメント  
 フラグメントは、特定のフレームワーク内の要素のサブツリー全体です。 サブツリーのルート ノードにある要素はフラグメント ルートと呼ばれます。 フラグメント ルートは、親がありませんが、他の何らかのフレームワーク (通常は [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ウィンドウ (HWND)) 内でホストされます。  
  
### <a name="hosts"></a>ホスト  
 すべてのフラグメントのルート ノードは、1 つの要素 (通常は [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ウィンドウ (HWND)) 内でホストする必要があります。 例外は、他の要素でホストされないデスクトップです。 カスタム コントロールのホストは、アプリケーション ウィンドウやトップ レベル コントロールのグループを含めることができるその他のウィンドウではなく、コントロール自体の HWND です。  
  
 フラグメントのホストは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] サービスを提供するうえで重要な役割を果たします。 このホストがフラグメント ルートへの移動を可能にし、いくつかの既定のプロパティを提供するため、カスタム プロバイダーはそれらを実装する必要がありません。  
  
## <a name="see-also"></a>関連項目
- [サーバー側 UI オートメーション プロバイダーの実装](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
