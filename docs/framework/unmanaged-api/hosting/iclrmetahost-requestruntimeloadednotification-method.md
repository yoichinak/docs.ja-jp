---
title: ICLRMetaHost::RequestRuntimeLoadedNotification メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61fce3e06b5245872f7061716e8d995dd5f5043c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984647"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification メソッド
共通言語ランタイム (CLR) バージョンが初めて読み込まれるが、開始していないときに呼び出されることが保証されるコールバック関数を提供します。 このメソッドは、 [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pCallbackFunction`  
 [in]新しいランタイムが読み込まれたときに呼び出されるコールバック関数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pCallbackFunction` が null です。|  
  
## <a name="remarks"></a>Remarks  
 コールバックは、次のように動作します。  
  
- 最初に、ランタイムが読み込まれる場合にのみ、コールバックが呼び出されます。  
  
- 同じランタイムの再入可能な負荷、コールバックは呼び出されません。  
  
- 再入不可能なランタイムの読み込み、コールバック関数の呼び出しがシリアル化します。  
  
 コールバック関数では、次のプロトタイプを持ちます。  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 コールバック関数のプロトタイプは次のとおりです。  
  
- `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 ホストが読み込みまたは再入可能の方法で読み込まれる別のランタイムが発生する場合、`pfnCallbackThreadSet`と`pfnCallbackThreadUnset`コールバック内で次のように関数を使用する必要がありますに用意されているパラメーター。  
  
- `pfnCallbackThreadSet` このような負荷が試みられる前に、実行時の負荷を引き起こす可能性のあるスレッドから呼び出す必要があります。  
  
- `pfnCallbackThreadUnset` スレッドは実行時の負荷が発生しない場合 (および初期コールバックから戻る前に) 呼び出す必要があります。  
  
- `pfnCallbackThreadSet` `pfnCallbackThreadUnset`はどちらも再入不可能な。  
  
> [!NOTE]
>  ホスト アプリケーションを呼び出してはならない`pfnCallbackThreadSet`と`pfnCallbackThreadUnset`の範囲外の`pCallbackFunction`パラメーター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMetaHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
