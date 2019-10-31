---
title: ICorDebugRegisterSet2::GetRegistersAvailable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: d0b6960a24e246c7a538e8ffc59fa380a4b8e2a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131367"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable メソッド
使用できるレジスタのビットマップを提供するバイト配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `numChunks`  
 [in] `availableRegChunks` 配列のサイズ。  
  
 `availableRegChunks`  
 入出力バイト配列。各ビットはレジスタに対応します。 レジスタが使用可能な場合は、レジスタの対応するビットが設定されます。  
  
## <a name="remarks"></a>Remarks  
 CorDebugRegister 列挙子の値は、異なるマイクロプロセッサのレジスタを指定します。 各値の上位5ビットは、`availableRegChunks` バイト配列のインデックスになります。 各値の下位3ビットは、インデックス付きバイト内のビット位置を識別します。 特定のレジスタを指定する `CorDebugRegister` 値を指定すると、マスク内のレジスタの位置は次のように決定されます。  
  
1. `availableRegChunks` 配列内の正しいバイトにアクセスするために必要なインデックスを抽出します。  
  
     `CorDebugRegister` 値 > > 3  
  
2. インデックス付きバイト内のビット位置を抽出します。ビットゼロは最下位ビットです。  
  
     `CorDebugRegister` 値 & 7  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
