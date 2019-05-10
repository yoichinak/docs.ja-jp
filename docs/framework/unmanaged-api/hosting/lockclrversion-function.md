---
title: LockClrVersion 関数
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aab3a2a367f6af1deeb1201d391af271a4bd45ac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584988"
---
# <a name="lockclrversion-function"></a>LockClrVersion 関数
により、ホストがプロセス内で、CLR を明示的に初期化する前に使用する共通言語ランタイム (CLR) のバージョンを決定します。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `hostCallback`  
 [in]初期化時に CLR によって呼び出される関数。  
  
 `pBeginHostSetup`  
 [in]初期化の CLR に通知するためにホストによって呼び出される関数を開始しています。  
  
 `pEndHostSetup`  
 [in]初期化の CLR に通知するためにホストによって呼び出される関数が完了しました。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく、WinError.h で定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|1 つ以上の引数が null です。|  
  
## <a name="remarks"></a>Remarks  
 ホスト呼び出し`LockClrVersion`CLR を初期化する前にします。 `LockClrVersion` すべてがコールバック型の 3 つのパラメーターを受け取る[FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)します。 この種類の定義は次のとおりです。  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 次の手順は、ランタイムの初期化時に発生します。  
  
1. ホスト呼び出し[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)またはその他のランタイム初期化関数の 1 つ。 または、ホストは、COM オブジェクトのアクティベーションを使用してランタイムを初期化する可能性があります。  
  
2. ランタイムがで指定された関数を呼び出す、`hostCallback`パラメーター。  
  
3. 指定された関数`hostCallback`続いて、次の一連の呼び出し。  
  
    - 指定された関数、`pBeginHostSetup`パラメーター。  
  
    - `CorBindToRuntimeEx` (または別のランタイム初期化関数)。  
  
    - [Iclrruntimehost::sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)します。  
  
    - [Iclrruntimehost::start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)します。  
  
    - 指定された関数、`pEndHostSetup`パラメーター。  
  
 すべての呼び出し`pBeginHostSetup`に`pEndHostSetup`1 つのスレッドまたはファイバーは、同じ論理スタックで発生する必要があります。 このスレッドは、対象スレッドと異なる場合が`hostCallback`が呼び出されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
