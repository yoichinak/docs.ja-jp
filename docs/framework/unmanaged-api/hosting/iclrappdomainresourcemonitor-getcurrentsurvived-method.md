---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408ef5419fbc2081d25ad442986ec8155bcb4c62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985193"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived メソッド
最後の完全なブロッキング ガベージ コレクション後に残っていると、現在のアプリケーション ドメインによって参照されるバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwAppDomainId`  
 [in]要求されたアプリケーション ドメインの ID。  
  
 `pAppDomainBytesSurvived`  
 [out]このアプリケーション ドメインによって保持されている最後のガベージ コレクションの後に残ったバイト数へのポインター。 完全なコレクションの後は、この番号は正確で完全なは。 短期コレクションの後にこの数は完全な可能性があります。 このパラメーターは、`null` に設定できます。  
  
 `pRuntimeBytesSurvived`  
 [out]最後のガベージ コレクションの後に残っているバイトの総数へのポインター。 完全なコレクションの後は、この数は、マネージ ヒープに保持されているバイト数を表します。 短期コレクションの後は、この数は、短期のジェネレーションにライブで保持されているバイト数を表します。 このパラメーターは、`null` に設定できます。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|COR_E_APPDOMAINUNLOADED|アプリケーション ドメインがアンロードされたか、存在しません。|  
  
## <a name="remarks"></a>Remarks  
 統計がフル ブロッキング ガベージ コレクション後にのみ更新されます。つまり、コレクションの中に、アプリケーションが停止するを含むすべてのジェネレーションのコレクションが発生します。 たとえば、<xref:System.GC.Collect?displayProperty=nameWithType>メソッドのオーバー ロードは、完全なブロッキング コレクションを実行します。 同時実行ガベージ コレクションでは、バック グラウンドで行われ、アプリケーションはブロックされません。  
  
 `GetCurrentSurvived`メソッドはアンマネージと同等のマネージ<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>プロパティ。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAppDomainResourceMonitor インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [アプリケーション ドメインのリソース監視](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
