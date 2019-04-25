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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d1c49e8762d00e3e154c598c2542c4a76b9b28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107498"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion 関数
作成、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトが指定されたバージョン情報に基づきます。  
  
 この関数は廃止されていますが、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]します。 代わりに、共通言語ランタイム (CLR) 2.0 のインターフェイスを取得、使用、 [iclrruntimeinfo::getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)メソッド CLSID_CLRDebuggingLegacy クラス識別子と IID_ICorDebug インターフェイス識別子を指定します。 CLR 4 のインターフェイスを取得します。 または、後で呼び出し、 [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数とクラス識別子 CLSID_CLRDebugging と IID_ICLRDebugging インターフェイス識別子を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `iDebuggerVersion`  
 [in]バージョンの`ICorDebug`デバッガーによって必要なことができます。 参照してください、 [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)有効な値の列挙体。  
  
 `szDebuggeeVersion`  
 [in]デバッグするには、アプリケーションまたはプロセスに関連付けられている、共通言語ランタイム バージョン。 参照してください、 [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)または[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)メソッドについては、この値を取得する方法。  
  
 `ppCordb`  
 [out]ポインターを受け取る場所、`ICorDebug`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく、WinError.h ファイルで定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`szDebuggeeVersion` または`ppCordb`が null の場合、または、バージョン文字列が正しくありません。|  
  
## <a name="remarks"></a>Remarks  
 `szDebuggeeVersion` MSCorDbi.dll の対応するバージョンにパラメーターがマップされます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
