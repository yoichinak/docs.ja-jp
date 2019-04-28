---
title: ICorDebugProcess::WriteMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e9d640fb1c9dae5bb195baa504e560ba8e45821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930300"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory メソッド
このプロセスでメモリの領域にデータを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in]A`CORDB_ADDRESS`データ メモリ領域のベース アドレスは、値が書き込まれます。 データ転送が発生する前に、システムは、ベース アドレスで始まる、指定したサイズのメモリ領域が書き込み用にアクセスできることを確認します。 アクセスできない場合、メソッドは失敗します。  
  
 `size`  
 [in]メモリ領域に書き込まれるバイト数。  
  
 `buffer`  
 [in]書き込むデータを格納するバッファー。  
  
 `written`  
 [out]このプロセスのメモリ領域に書き込まれたバイト数を受け取る変数へのポインター。 場合`written`が null の場合、このパラメーターは無視されます。  
  
## <a name="remarks"></a>Remarks  
 データは、ブレークポイントの背後に自動的に書き込まれます。 .NET framework version 2.0 では、ネイティブ デバッガーは、命令ストリームにブレークポイントを挿入するのにこのメソッドを使用する必要があります。 使用[icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)代わりにします。  
  
 `WriteMemory`メソッドは、マネージ コードの外側でのみ使用する必要があります。 このメソッドは、誤って使用すると、ランタイムを破壊できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
