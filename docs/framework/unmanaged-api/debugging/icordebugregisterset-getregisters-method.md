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
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178546"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters メソッド
ビット マスクで指定されている各レジスタ (現在コードを実行しているコンピューター上) の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mask`  
 [in]取得するレジスタ値を指定するビット マスク。 各ビットはレジスタに対応します。 ビットが 1 に設定されている場合、レジスタの値が取得されます。それ以外の場合、レジスタの値は取得されません。  
  
 `regCount`  
 [in]取得するレジスタ値の数。  
  
 `regBuffer`  
 [アウト]レジスタの`CORDB_REGISTER`値を受け取るオブジェクトの配列。  
  
## <a name="remarks"></a>解説  
 配列のサイズは、ビット マスク内の 1 に設定されたビット数と等しくする必要があります。 パラメーター`regCount`は、レジスタ値を受け取るバッファー内の要素の数を指定します。 マスクで`regCount`示されるレジスタの数に対して値が小さすぎる場合は、番号が大きいレジスタはセットから切り捨てられます。 値が`regCount`大きすぎると、未使用`regBuffer`の要素は変更されません。  
  
 ビット マスクが使用できないレジスタを指定している場合`GetRegisters`、そのレジスタの不確定な値を返します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)
