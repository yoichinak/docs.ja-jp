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
ms.openlocfilehash: eaf5b9980d55b0efb473b4631a8c052b013d0796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137253"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory メソッド
このプロセスのメモリ領域にデータを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 からデータが書き込まれるメモリ領域のベースアドレスである `CORDB_ADDRESS` 値。 データ転送が行われる前に、システムは、ベースアドレスを開始位置として、指定したサイズのメモリ領域が書き込み可能であることを確認します。 アクセスできない場合、メソッドは失敗します。  
  
 `size`  
 からメモリ領域に書き込まれるバイト数。  
  
 `buffer`  
 から書き込むデータを格納するバッファー。  
  
 `written`  
 入出力このプロセスのメモリ領域に書き込まれたバイト数を受け取る変数へのポインター。 `written` が NULL の場合、このパラメーターは無視されます。  
  
## <a name="remarks"></a>Remarks  
 データは、ブレークポイントの背後に自動的に書き込まれます。 .NET Framework バージョン2.0 では、ネイティブデバッガーは、このメソッドを使用して命令ストリームにブレークポイントを挿入することはできません。 代わりに[ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)を使用してください。  
  
 `WriteMemory` メソッドは、マネージコードの外部でのみ使用する必要があります。 不適切に使用された場合、このメソッドはランタイムを破損する可能性があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
