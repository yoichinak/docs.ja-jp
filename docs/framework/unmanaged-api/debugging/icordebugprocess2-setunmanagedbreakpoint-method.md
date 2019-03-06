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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b374720bd7bdad48222da006b809702de6462a62
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472786"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint メソッド
ネイティブ イメージを指定したオフセットで非管理対象のブレークポイントを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]A`CORDB_ADDRESS`ネイティブ イメージのオフセットを指定するオブジェクト。  
  
 `bufsize`  
 [in]サイズ (バイト単位) の`buffer`配列。  
  
 `buffer`  
 [out]ブレークポイントで置き換えられるオペコードを含む配列。  
  
 `bufLen`  
 [out]返されるバイト数へのポインター、`buffer`配列。  
  
## <a name="remarks"></a>Remarks  
 ネイティブ イメージのオフセットが共通言語ランタイム (CLR) 内にある場合は、ブレークポイントは無視されます。 これにより、デバッガーでブレークポイントが設定されている場合、帯域外のブレークポイントのディスパッチを回避するために CLR ができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
