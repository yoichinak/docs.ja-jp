---
title: クライアント側 UI オートメーション プロバイダーの実装
description: クライアント側 UI オートメーションプロバイダーの実装について説明します。 クライアント側プロバイダーを配布、登録、および構成する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 867293c00d0724e27f5163f3ae8be43aca30cfe8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164394"
---
# <a name="client-side-ui-automation-provider-implementation"></a>クライアント側 UI オートメーション プロバイダーの実装
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]Microsoft オペレーティングシステムでは、Win32、Windows フォーム、など、いくつかの異なるフレームワークが使用されてい [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ます。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] は、UI 要素に関する情報をクライアントに公開します。 ただし、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 自体は、それらのフレームワークに存在する各種のコントロールや、それらから情報を抽出するために必要な手法を認識しているわけではありません。 その代わりに、このタスクをプロバイダーと呼ばれるオブジェクトに任せます。 プロバイダーは、特定のコントロールから情報を抽出し、その情報を [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に渡します。次に UI オートメーションが、その情報を一貫性のある方法でクライアントに提示します。  
  
 プロバイダーは、サーバー側とクライアント側のどちらにも配置できます。 サーバー側プロバイダーは、コントロール自体によって実装されます。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] で作成されたすべてのサードパーティ コントロールを考慮してプロバイダーを実装しています。  
  
 ただし、Win32 や Windows フォームのような古いコントロールは、を直接サポートしていません [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。 これらのコントロールは、代わりにクライアント プロセス内のプロバイダーによって処理され、プロセス間通信を使用して、たとえば、コントロール間でのウィンドウ メッセージを監視することで、コントロールに関する情報を取得します。 このようなクライアント側プロバイダーは、プロキシと呼ばれることがあります。  
  
 Windows Vista には、標準の Win32 および Windows フォームコントロール用のプロバイダーが用意されています。 また、フォールバックプロバイダーは、別の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] サーバー側プロバイダーまたはプロキシによって処理されないが、Microsoft Active Accessibility 実装があるコントロールに対して、部分的なサポートを提供します。 これらすべてのプロバイダーは、自動的に読み込まれ、クライアント アプリケーションから使用できるようになります。  
  
 Win32 および Windows フォームコントロールのサポートの詳細については、「 [UI オートメーションによる標準コントロールのサポート](ui-automation-support-for-standard-controls.md)」を参照してください。  
  
 アプリケーションが他のクライアント側プロバイダーを登録することもできます。  
  
<a name="Distributing_Client-Side_Providers"></a>
## <a name="distributing-client-side-providers"></a>クライアント側プロバイダーを配布する  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、クライアント側プロバイダーがマネージ コード アセンブリ内に見つかることを前提としています。 このアセンブリ内の名前空間は、アセンブリと同じ名前を持つ必要があります。 たとえば、ContosoProxies.dll というアセンブリには、ContosoProxies という名前空間が含まれます。 その名前空間内に、 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> クラスを作成します。 静的 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> フィールドの実装内に、プロバイダーを記述した <xref:System.Windows.Automation.ClientSideProviderDescription> 構造体の配列を作成します。  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>
## <a name="registering-and-configuring-client-side-providers"></a>クライアント側プロバイダーを登録および構成する  
 ダイナミックリンクライブラリ (DLL) 内のクライアント側プロバイダーは、を呼び出すことによって読み込まれ <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A> ます。 クライアント アプリケーションでは、プロバイダーを利用するために、それ以上のアクションは必要ありません。  
  
 クライアント独自のコードで実装されたプロバイダーは、 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>を使用して登録されます。 このメソッドは引数として、 <xref:System.Windows.Automation.ClientSideProviderDescription> 構造体の配列を受け取ります。各構造体では、次のプロパティが指定されます。  
  
- プロバイダー オブジェクトを作成するコールバック関数。  
  
- プロバイダーが使用されるコントロールのクラス名。  
  
- プロバイダーが使用されるアプリケーションのイメージ名 (通常は実行可能ファイルの完全名)。  
  
- クラス名と、ターゲット アプリケーションで検出されたウィンドウ クラスを照合する方法を制御するフラグ。  
  
 最後の 2 つのパラメーターは省略できます。 クライアントでは、異なるアプリケーションに対して異なるプロバイダーを使用する必要がある場合、ターゲット アプリケーションのイメージ名を指定することができます。 たとえば、クライアントは、複数のビューパターンをサポートする既知のアプリケーションの Win32 リストビューコントロールに対して1つのプロバイダーを使用し、それ以外の別の既知のアプリケーションの同様のコントロールに対して別のプロバイダーを使用する場合があります。  
  
## <a name="see-also"></a>関連項目

- [クライアント側 UI オートメーション プロバイダーの作成](create-a-client-side-ui-automation-provider.md)
- [クライアント アプリケーションに UI オートメーション プロバイダーを実装する](implement-ui-automation-providers-in-a-client-application.md)
