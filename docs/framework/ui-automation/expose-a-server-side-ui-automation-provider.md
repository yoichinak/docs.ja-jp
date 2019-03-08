---
title: サーバー側 UI オートメーション プロバイダーの公開
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expose a server-side UI Automation provider
- UI Automation, server-side provider, exposing
- server-side UI Automation provider, exposing
ms.assetid: 55d419c0-2201-4101-90c9-2888df4dbb47
ms.openlocfilehash: d2964e8cee509062353e0eb7aed998c49dd86dbe
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673302"
---
# <a name="expose-a-server-side-ui-automation-provider"></a>サーバー側 UI オートメーション プロバイダーの公開
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックには、 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> ウィンドウにホストされているサーバー側 UI オートメーション プロバイダーを公開する方法を示すコード例が含まれています。  
  
 この例は、WM_GETOBJECT (クライアント アプリケーションがウィンドウに関する情報を要求したときに、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コア サービスによって送信されるメッセージ) をトラップするためのウィンドウ プロシージャをオーバーライドします。  
  
## <a name="example"></a>例  
 [!code-csharp[UIAFragmentProvider_snip#116](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#116)]
 [!code-vb[UIAFragmentProvider_snip#116](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#116)]  
  
## <a name="see-also"></a>関連項目
- [UI オートメーション プロバイダーの概要](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [サーバー側 UI オートメーション プロバイダーの実装](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
