---
title: ICorDebugRemote::CreateProcessEx メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744777"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx メソッド
デバッガーでのリモート コンピューター上のプロセスを起動します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pRemoteTarget`  
 [in]ポインター、 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)します。 プロセスの起動をリモート コンピューターを決定するために使用します。  
  
 `lpApplicationName`  
 [in]実行中のプロセスによって実行されるモジュールを指定する null で終わる文字列へのポインター。 モジュールは、呼び出し元のプロセスのセキュリティ コンテキストで実行されます。  
  
 `lpCommandLine`  
 [in]実行中のプロセスによって実行されるコマンドラインを指定する null で終わる文字列へのポインター。  
  
 `lpProcessAttributes`  
 [in]リモート デバッグに使用されていません。  
  
 `lpThreadAttributes`  
 [in]リモート デバッグに使用されていません。  
  
 `bInheritHandles`  
 [in]リモート デバッグに使用されていません。  
  
 `dwCreationFlags`  
 [in]リモート デバッグに使用されていません。  
  
 `lpEnvironment`  
 [in]新しいプロセスの環境ブロックへのポインター。  
  
 `lpCurrentDirectory`  
 [in]プロセスの現在のディレクトリにフルパスを指定する null で終わる文字列へのポインター。 このパラメーターが null の場合、新しいプロセスは、呼び出し元プロセスとして同じの現在のドライブとディレクトリがあります。  
  
 `lpStartupInfo`  
 [in]リモート デバッグに使用されていません。  
  
 `lpProcessInformation`  
 [in]リモート デバッグに使用されていません。  
  
 `debuggingFlags`  
 [in]リモート デバッグに使用されていません。  
  
 `ppProcess`  
 [out]プロセスを表す「ICorDebugProcess インターフェイス」オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 デバッグ、リモート コンピューターに返される「ICorDebugProcess インターフェイス」プロセスが正常に起動します。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 リモート コンピューター上のプロセスを起動してデバッグ「ICorDebugProcess インターフェイス」を返すことができません。  
  
## <a name="remarks"></a>Remarks  
 Silverlight では、混合モード デバッグはサポートされていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemote インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
