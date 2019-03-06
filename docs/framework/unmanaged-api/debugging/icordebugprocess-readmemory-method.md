---
title: ICorDebugProcess::ReadMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218279684304b766a9bf009f5891ac4910254a3c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492167"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory メソッド
このプロセスのメモリの指定された領域を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in]A`CORDB_ADDRESS`読み取られるメモリのベース アドレスを指定する値。  
  
 `size`  
 [in]メモリから読み取られるバイト数。  
  
 `buffer`  
 [out]メモリの内容を受け取るバッファー。  
  
 `read`  
 [out]バイト数へのポインターは、指定されたバッファーに転送されます。  
  
## <a name="remarks"></a>Remarks  
 `ReadMemory`メソッドは主にデバッグ対象のアンマネージ部分で使用されているメモリ領域を検査する相互運用機能デバッグで使用されるものです。 このメソッドは、Microsoft intermediate language (MSIL) コードとネイティブ JIT コンパイル コードの読み取りにも使用できます。  
  
 返されるデータから管理対象のブレークポイントは削除されます、`buffer`パラメーター。 によってネイティブのブレークポイントの設定の調整は行われません[icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)します。  
  
 プロセス メモリのキャッシュは実行されません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
