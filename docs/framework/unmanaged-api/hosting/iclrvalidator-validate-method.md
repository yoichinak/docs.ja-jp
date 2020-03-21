---
title: ICLRValidator::Validate メソッド
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178062"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate メソッド
指定されたファイル内のポータブル実行可能 (PE) または Microsoft 中間言語 (MSIL) を検証します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a>パラメーター  
 `veh`  
 [in]検証エラーを処理`IVEHandler`するインスタンスへのポインター。  
  
 `ulAppDomainId`  
 [in]現在<xref:System.AppDomain>の .  
  
 `ulFlags`  
 [in]実行する検証の種類を示す[、検証フラグ](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)の値の組み合わせ。  
  
 `ulMaxError`  
 [in]検証を終了するまでに許容されるエラーの最大数。  
  
 `token`  
 [in]未使用。  
  
 `fileName`  
 [in]検証するファイルの名前。  
  
 `pe`  
 [in]ファイル バッファーへのポインター。  
  
 `ulSize`  
 [in]検証するファイルのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`Validate`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージ コードを実行できない状態または呼び出しを正常に処理できない状態にあります。|  
|HOST_E_TIMEOUT|通話がタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバが待機しているときにイベントがキャンセルされました。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドがE_FAILを返すと、CLR はプロセス内で使用できなくなります。 ホスト メソッドへの後続の呼び出しは、HOST_E_CLRNOTAVAILABLEを返します。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** イバリデーター.idl、イバリデーター.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRValidator インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
