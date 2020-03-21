---
title: CreateDebuggingInterfaceFromVersion 関数
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176449"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion 関数
指定されたバージョン情報に基づいて[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトを作成します。  
  
 この関数は、.NET Framework 4 では廃止されました。 代わりに、共通言語ランタイム (CLR) 2.0 のインターフェイスを取得するには、[メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)を使用して、クラス識別子CLSID_CLRDebuggingLegacyとインターフェイス識別子IID_ICorDebugを指定します。 CLR 4 以降のインターフェイスを取得するには[、CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数を呼び出し、クラス識別子CLSID_CLRDebuggingとインターフェイス識別子IID_ICLRDebuggingを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `iDebuggerVersion`  
 [in]`ICorDebug`デバッガーが予期するバージョンです。 有効な値については、[列挙](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)体を参照してください。  
  
 `szDebuggeeVersion`  
 [in]デバッグするアプリケーションまたはプロセスに関連付けられている共通言語ランタイムのバージョン。 この値の[取得](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)の詳細については[、メソッドを](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)参照してください。  
  
 `ppCordb`  
 [アウト]`ICorDebug`オブジェクトへのポインターを受け取る位置。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、WinError.h ファイルで定義されている標準 COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`szDebuggeeVersion`または`ppCordb`null であるか、バージョン文字列が正しくありません。|  
  
## <a name="remarks"></a>解説  
 パラメーター`szDebuggeeVersion`は、対応するバージョンの MSCorDbi.dll にマップされます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
