---
title: ICorDebugDataTarget::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 278320391615eddaa8ba878ef87f802f30cddb95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122022"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext メソッド
指定されたスレッドの現在のスレッドコンテキストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwThreadID`  
 からコンテキストを取得するスレッドの識別子。 識別子はオペレーティングシステムによって定義されます。  
  
 `contextFlags`  
 からコンテキストのどの部分を読み取る必要があるかを示す、プラットフォームに依存するフラグのビットごとの組み合わせ。  
  
 `contextSize`  
 [入力] `pContext` のサイズ。  
  
 `pContext`  
 入出力スレッドコンテキストが格納されるバッファー。  
  
## <a name="remarks"></a>Remarks  
 Windows プラットフォームでは、`pContext` は、の `CONTEXT` 構造 (Winnt.h で定義されています) である必要があります。これは[、のコンピューター](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)の種類に対応しています。 `contextFlags` には、`CONTEXT` 構造体の `ContextFlags` フィールドと同じ値を指定する必要があります。 `CONTEXT` 構造体はプロセッサに固有です。詳細については、「Winnt.h ファイル」を参照してください。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
