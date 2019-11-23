---
title: UI オートメーション プロバイダーの概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 417cc17986fa1481505a88d778dcaa747860efbe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447978"
---
# <a name="ui-automation-providers-overview"></a>UI オートメーション プロバイダーの概要
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。  
  
 UI オートメーション プロバイダーを使用すれば、コントロールで UI オートメーション クライアント アプリケーションと通信することができます。 一般に、各コントロールまたは [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 内のその他の要素はプロバイダーによって表現されます。 プロバイダーは、要素に関する情報を公開し、必要に応じて、クライアント アプリケーションがコントロールと対話できるようにするコントロール パターンを実装します。  
  
 通常、クライアント アプリケーションはプロバイダーと直接連動する必要はありません。 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]、または [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] フレームワークを使用するアプリケーション内の標準コントロールのほとんどが自動的に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] システムに公開されます。 カスタム コントロールを実装するアプリケーションがそれらのコントロール用の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロバイダーを実装することもできます。クライアント アプリケーションがそれらにアクセスするために特別な手順を実行する必要はありません。  
  
 このトピックでは、コントロールの開発者が [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] と [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] のウィンドウのコントロール専用に [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] プロバイダーを実装する方法について説明します。  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>プロバイダーの種類  
 UI オートメーション プロバイダーは、クライアント側プロバイダーとサーバー側プロバイダーの 2 つのカテゴリに分類されます。  
  
### <a name="client-side-providers"></a>クライアント側プロバイダー  
 クライアント側プロバイダーは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]をサポートしていないか部分的にサポートしているアプリケーションと通信する UI オートメーション クライアントによって実装されます。 Client-side providers usually communicate with the server across the process boundary by sending and receiving Windows messages.  
  
 Because UI Automation providers for controls in [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms, or [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] applications are supplied as part of the operating system, client applications seldom have to implement their own providers, and this overview does not cover them further.  
  
### <a name="server-side-providers"></a>サーバー側プロバイダー  
 Server-side providers are implemented by custom controls or by applications that are based on a UI framework other than [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms, or [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 また、サーバー側プロバイダーは、サーバーからクライアントに要求するインターフェイスを [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コア システムに公開することにより、プロセス境界を越えてクライアント アプリケーションと通信します。  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>UI オートメーション プロバイダーの概念  
 ここでは、UI オートメーション プロバイダーを実装するために理解しておく必要があるいくつかの重要な概念について簡単に説明します。  
  
### <a name="elements"></a>Elements  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素は、UI オートメーション クライアントからアクセス可能な [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] の一部です。 例として、アプリケーション ウィンドウ、ペイン、ボタン、ツールヒント、リスト ボックス、およびリスト項目が含まれています。  
  
### <a name="navigation"></a>ナビゲーション  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーとしてクライアントに公開されます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、要素間を移動することによって、ツリーを構成します。 ナビゲーションは、親、兄弟、または子を指す要素ごとに、プロバイダーによって有効にされます。  
  
 For more information on the client view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Views  
 次の表に示すように、クライアントは 3 つのプリンシパル ビューで [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーを表示できます。  
  
|||  
|-|-|  
|列ビュー|すべての要素が含まれます。|  
|コントロール ビュー|コントロールである要素が含まれます。|  
|コンテンツ ビュー|コンテンツである要素が含まれます。|  
  
 For more information on client views of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
 コンテンツ要素またはコントロール要素としての要素の定義はプロバイダー実装で行う必要があります。 コントロール要素はコンテンツ要素であることもないこともありますが、コンテンツ要素はすべてコントロール要素です。  
  
### <a name="frameworks"></a>Frameworks  
 フレームワークは、画面のある領域で子コントロール、ヒット テスト、およびレンダリングを管理するコンポーネントです。 たとえば、HWND とも呼ばれる [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ウィンドウは、メニュー バー、ステータス バー、ボタンなどの [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素が複数含まれるフレームワークとして機能することができます。  
  
 リスト ボックスやツリー ビューなどの[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] コンテナー コントロールは、子項目をレンダリングしたり、それらに対してヒット テストを実行したりするための独自のコードが含まれているため、フレームワークと見なされます。 これに対して、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] リスト ボックスは、包含する [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ウィンドウによってレンダリングやヒット テストが処理されるため、フレームワークではありません。  
  
 アプリケーション内の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] はさまざまなフレームワークで構成することができます。 For example, an HWND application window might contain Dynamic HTML (DHTML) which in turn contains a component such as a combo box in an HWND.  
  
### <a name="fragments"></a>フラグメント  
 フラグメントは、特定のフレームワーク内の要素のサブツリー全体です。 サブツリーのルート ノードにある要素はフラグメント ルートと呼ばれます。 フラグメント ルートは、親がありませんが、他の何らかのフレームワーク (通常は [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ウィンドウ (HWND)) 内でホストされます。  
  
### <a name="hosts"></a>ホスト  
 すべてのフラグメントのルート ノードは、1 つの要素 (通常は [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ウィンドウ (HWND)) 内でホストする必要があります。 例外は、他の要素でホストされないデスクトップです。 カスタム コントロールのホストは、アプリケーション ウィンドウやトップ レベル コントロールのグループを含めることができるその他のウィンドウではなく、コントロール自体の HWND です。  
  
 フラグメントのホストは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] サービスを提供するうえで重要な役割を果たします。 このホストがフラグメント ルートへの移動を可能にし、いくつかの既定のプロパティを提供するため、カスタム プロバイダーはそれらを実装する必要がありません。  
  
## <a name="see-also"></a>関連項目

- [サーバー側 UI オートメーション プロバイダーの実装](server-side-ui-automation-provider-implementation.md)
