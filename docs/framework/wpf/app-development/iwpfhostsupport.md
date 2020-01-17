---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 4855fae2954e5650d8c9bbb81153ebe64249a867
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740187"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
プレゼンテーションの cluster.exe を介して [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] コンテンツをホストするアプリケーションは、このインターフェイスを実装して、ホストとプレゼンテーションの cluster.exe の間の統合ポイントを提供します。  
  
## <a name="remarks"></a>Remarks  
 Web ブラウザーなどの Win32 アプリケーションは、XAML ブラウザーアプリケーション (Xbap) やルース XAML などの WPF コンテンツをホストできます。 WPF コンテンツをホストするために、Win32 アプリケーションは[WebBrowser コントロール](https://go.microsoft.com/fwlink/?LinkId=97911)のインスタンスを作成します。 ホストされるようにするために、WPF は、ホストされている WPF コンテンツをホストに提供し、 [WebBrowser コントロール](https://go.microsoft.com/fwlink/?LinkId=97911)に表示するための、プレゼンテーション用の cluster.exe インスタンスを作成します。  
  
 `IWpfHostSupport` によって有効にされた統合によって、次のことを行うことができます。  
  
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
