---
title: ICorDebugRegisterSet2::GetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 8e5583acfe338c185200c0b8e41b7d6e051fa146
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131352"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters メソッド
指定されたビットマスクによって指定された各レジスタの値を取得します (コードが現在実行されているプラットフォーム用)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `maskCount`  
 から`mask` 配列のサイズ (バイト単位)。  
  
 `mask`  
 からバイト配列。各ビットはレジスタに対応します。 ビットが1の場合は、対応するレジスタの値が取得されます。  
  
 `regCount`  
 から取得するレジスタ値の数。  
  
 `regBuffer`  
 入出力`CORDB_REGISTER` オブジェクトの配列。各オブジェクトは、レジスタの値を受け取ります。  
  
## <a name="remarks"></a>Remarks  
 `GetRegisters` メソッドは、マスクによって指定されたレジスタから値の配列を返します。 配列に、マスクビットが設定されていないレジスタの値が含まれていません。 したがって、`regBuffer` 配列のサイズは、マスク内の1の数と同じである必要があります。 `regCount` の値が、マスクによって示されるレジスタの数に対して小さすぎる場合、より上位の番号付きレジスタの値はセットから切り捨てられます。 `regCount` が大きすぎる場合、未使用の `regBuffer` 要素は変更されません。  
  
 使用できないレジスタがマスクによって示されている場合、そのレジスタに対して不確定な値が返されます。  
  
 `ICorDebugRegisterSet2::GetRegisters` メソッドは、64を超えるレジスタを持つプラットフォームに必要です。 たとえば、IA64 には128汎用レジスタと128浮動小数点レジスタがあるため、ビットマスクには64ビット以上のビットが必要です。  
  
 X86 などのプラットフォームの場合と同様に、64以上のレジスタがない場合、`GetRegisters` メソッドは実際には、`mask` バイト配列のバイトを `ULONG64` に変換し、次に、は、次のように入力します[。](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)。 `ULONG64` マスクを受け取ります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
