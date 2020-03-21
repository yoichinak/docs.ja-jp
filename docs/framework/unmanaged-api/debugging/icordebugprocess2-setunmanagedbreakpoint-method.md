---
title: ICorDebugProcess2::SetUnmanagedBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178645"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint メソッド
指定したネイティブ イメージ オフセットにアンマネージ ブレークポイントを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in]ネイティブ`CORDB_ADDRESS`イメージ オフセットを指定するオブジェクト。  
  
 `bufsize`  
 [in]`buffer`配列のサイズ (バイト単位)。  
  
 `buffer`  
 [アウト]ブレークポイントに置き換えられるオペコードを含む配列。  
  
 `bufLen`  
 [アウト]`buffer`配列に返されるバイト数へのポインター。  
  
## <a name="remarks"></a>解説  
 ネイティブ イメージのオフセットが共通言語ランタイム (CLR) 内にある場合、ブレークポイントは無視されます。 これにより、ブレークポイントがデバッガーによって設定されている場合、CLR は帯域外ブレークポイントをディスパッチしないようにできます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
