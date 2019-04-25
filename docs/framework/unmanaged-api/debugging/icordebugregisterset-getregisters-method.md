---
title: ICorDebugRegisterSet::GetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b417685361126951470571e2440cc842ab1c94fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153908"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters メソッド
各レジスタの値を取得します (現在のコードを実行しているコンピューター) でビット マスクによって指定されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mask`  
 [in]値が取得するにはどのレジスタを指定するビット マスク。 各ビットは、レジスタに対応します。 ビットは 1 つに設定されている場合は、レジスタの値が取得されます。それ以外の場合、レジスタの値は取得されません。  
  
 `regCount`  
 [in]取得するレジスタの値の数。  
  
 `regBuffer`  
 [out]配列の`CORDB_REGISTER`オブジェクト、レジスタの値を受信します。  
  
## <a name="remarks"></a>Remarks  
 配列のサイズは、ビット マスクのいずれかに設定するビット数に等しい必要があります。 `regCount`パラメーターがレジスタの値を受け取るバッファー内の要素の数を指定します。 場合、`regCount`マスクで指定したレジスタの数の値が小さすぎる、セットから大きい番号のレジスタは切り捨てられます。 場合、`regCount`値が大きすぎて、未使用`regBuffer`要素は変更できません。  
  
 ビット マスクが使用できないレジスタを指定する場合`GetRegisters`そのレジスタの中間の値を返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
