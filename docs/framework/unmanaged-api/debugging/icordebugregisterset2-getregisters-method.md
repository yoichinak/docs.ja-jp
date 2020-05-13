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
ms.openlocfilehash: b7a356d80d63fae65191bbf4fc0a23d7e02004c9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378228"
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
 から配列のサイズ (バイト単位) `mask` 。  
  
 `mask`  
 からバイト配列。各ビットはレジスタに対応します。 ビットが1の場合は、対応するレジスタの値が取得されます。  
  
 `regCount`  
 から取得するレジスタ値の数。  
  
 `regBuffer`  
 入出力オブジェクトの配列 `CORDB_REGISTER` 。各オブジェクトは、レジスタの値を受け取ります。  
  
## <a name="remarks"></a>Remarks  
 メソッドは、 `GetRegisters` マスクによって指定されたレジスタから値の配列を返します。 配列に、マスクビットが設定されていないレジスタの値が含まれていません。 したがって、配列のサイズは `regBuffer` マスク内の1の数と同じである必要があります。 の値 `regCount` がマスクで示されているレジスタの数に対して小さすぎる場合、番号が大きいレジスタの値はセットから切り捨てられます。 `regCount`が大きすぎる場合、未使用の `regBuffer` 要素は変更されません。  
  
 使用できないレジスタがマスクによって示されている場合、そのレジスタに対して不確定な値が返されます。  
  
 メソッドは、 `ICorDebugRegisterSet2::GetRegisters` 64 を超えるレジスタを持つプラットフォームに必要です。 たとえば、IA64 には128汎用レジスタと128浮動小数点レジスタがあるため、ビットマスクには64ビット以上のビットが必要です。  
  
 X86 などのプラットフォームの場合と同様に、64以上のレジスタがない場合、メソッドは実際にはバイト配列のバイトをに変換し、次に、 `GetRegisters` `mask` `ULONG64` マスクを[ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md)取得する、は、のようにすることができます。 `ULONG64`  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet インターフェイス](icordebugregisterset-interface.md)
