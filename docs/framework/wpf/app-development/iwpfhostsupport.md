---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 994e5146e9cf49a9b31396d0b51e7be83bbb3cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964784"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
プレゼンテーションの cluster.exe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]を使用してコンテンツをホストするアプリケーションは、このインターフェイスを実装して、ホストとプレゼンテーションの cluster.exe 間の統合ポイントを提供します。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]Web ブラウザーなどのアプリケーションは、 [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] XAML など[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]のコンテンツをホストできます。 コンテンツを[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]ホストする[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]ために、アプリケーションは[WebBrowser コントロール](https://go.microsoft.com/fwlink/?LinkId=97911)のインスタンスを作成します。 ホストされるため[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]に、は、 [WebBrowser コントロール](https://go.microsoft.com/fwlink/?LinkId=97911)に表示するホストにホストさ[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]れたコンテンツを提供する、プレゼンテーションの cluster.exe のインスタンスを作成します。  
  
 によって有効`IWpfHostSupport`にされた統合によって、次のことを行うことができます。  
  
- ホストアプリケーションが興味を持っている未加工の入力デバイス (ヒューマンインターフェイスデバイス) を検出し、登録します。  
  
- 登録されている未加工の入力デバイスから入力メッセージを受信し、適切なメッセージをホストアプリケーションに転送します。  
  
- ホストアプリケーションに対して、カスタムの進行状況とエラーユーザーインターフェイスを照会します。  
  
> [!NOTE]
> この API は、ローカル クライアント コンピューターでの使用のみを目的とし、サポートされています。  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|PresentationHost.exe が、ホスト アプリケーションに必要な未加工入力デバイス (ヒューマン インターフェイス デバイス) を検出できるようにします。|  
|[FilterInputMessage](filterinputmessage.md)|E_NOTIMPL が返されない限り、メッセージを受信するたびに PresentationHost.exe によって呼び出されます。|  
|[GetCustomUI](getcustomui.md)|既定では、プレゼンテーションの cluster.exe によって、WPF コンテンツが配置されるときに表示される、独自の配置の進行状況と配置エラーのユーザーインターフェイスが提供されます。|
