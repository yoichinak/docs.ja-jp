---
title: ICorDebugRegisterSet::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: db4f9bc6277015055cbcdb509628f2862a71dbc4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127154"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a>ICorDebugRegisterSet::GetThreadContext メソッド
現在のスレッドのコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `contextSize`  
 から`context` 配列のサイズ (バイト単位)。  
  
 `context`  
 [入力、出力]現在のプラットフォームの Win32 `CONTEXT` 構造体を構成するバイト配列。  
  
## <a name="remarks"></a>Remarks  
 スレッドが一時的に変更されている "ハイジャック" 状態である可能性があるため、デバッガーは Win32 `GetThreadContext` 関数の代わりにこの関数を呼び出す必要があります。 返されるデータは、現在のプラットフォームの Win32 `CONTEXT` 構造体です。  
  
 非リーフフレームの場合、クライアントは、テキストボックス[:: GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)を使用して、どのレジスタが有効であるかを確認する必要があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
