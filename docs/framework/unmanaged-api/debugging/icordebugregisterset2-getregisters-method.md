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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136696"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters メソッド
各レジスタの値を取得します (コードが現在実行されているプラットフォーム) の特定のビット マスクによって指定されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `maskCount`  
 [in]サイズ (バイト単位) の`mask`配列。  
  
 `mask`  
 [in]バイトの配列を各ビットは、レジスタに対応します。 ビットが 1 の場合は、対応するレジスタの値が取得されます。  
  
 `regCount`  
 [in]取得するレジスタの値の数。  
  
 `regBuffer`  
 [out]配列の`CORDB_REGISTER`オブジェクト、レジスタの値を受信します。  
  
## <a name="remarks"></a>Remarks  
 `GetRegisters`マスクによって指定されているレジスタの値の配列を返します。 配列にマスク ビットが設定されていないレジスタの値が含まれていません。 したがってのサイズ、`regBuffer`配列は、マスク内の 1 の数と同じである必要があります。 場合の値`regCount`のセットからマスク、大きい番号のレジスタの値で指定したレジスタの数は切り捨てられますが、小さすぎます。 場合`regCount`が大きすぎる、未使用`regBuffer`要素は変更できません。  
  
 使用できないレジスタがマスクによって示される場合、は、そのレジスタの中間の値が返されます。  
  
 `ICorDebugRegisterSet2::GetRegisters`メソッドがプラットフォーム 64 を超えるレジスタがあるに必要です。 たとえば、IA64 が 128 の汎用レジスタと 128 の浮動小数点レジスタ、64 ビット マスクのビットを超える必要があります。  
  
 同様に、x86 などのプラットフォームでは、64 を超えるレジスタを持たない場合、`GetRegisters`メソッドは実際には、バイト、変換、`mask`のバイト配列、`ULONG64`号餧ェヒェマル、 [ICorDebugRegisterSet:。GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)メソッド、`ULONG64`マスク。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
