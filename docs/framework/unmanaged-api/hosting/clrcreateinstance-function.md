---
title: CLRCreateInstance 関数
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9dc3f87ce727076d561923fe35495bbfe4419e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768130"
---
# <a name="clrcreateinstance-function"></a>CLRCreateInstance 関数
次の 3 つのインターフェイスの 1 つを提供します。[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)、または[ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `clsid`  
 [in]3 つのクラス識別子のいずれか:CLSID_CLRMetaHost、CLSID_CLRMetaHostPolicy、または CLSID_CLRDebugging します。  
  
 `riid`  
 [in]次の 3 つのインターフェイス id (Iid) のいずれか:IID_ICLRMetaHost、IID_ICLRMetaHostPolicy、または IID_ICLRDebugging します。  
  
 `ppInterface`  
 [out]3 つのインターフェイスのいずれか:[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)、または[ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`ppInterface` が null です。|  
  
## <a name="remarks"></a>Remarks  
 次の表は、サポートされている組み合わせ`clsid`と`riid`します。  
  
|`clsid`|`riid`|  
|--------------|------------|  
|CLSID_CLRMetaHost|IID_ICLRMetaHost|  
|CLSID_CLRMetaHostPolicy|IID_ICLRMetaHostPolicy|  
|CLSID_CLRDebugging|IID_ICLRDebugging|  
  
 次のコードは、使用する方法を示しています。`CLRCreateInstance`に 3 つすべてのインターフェイスを取得します。  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
