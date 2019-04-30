---
title: ICorDebugModule::GetBaseAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 763f2872099fac87138b7e1ab058c60475892b0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994917"
---
# <a name="icordebugmodulegetbaseaddress-method"></a>ICorDebugModule::GetBaseAddress メソッド
モジュールのベース アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAddress`  
 [out]A`CORDB_ADDRESS`モジュールのベース アドレスを指定します。  
  
## <a name="remarks"></a>Remarks  
 ネイティブ モジュールの場合 (つまり、モジュールは、ネイティブ イメージ ジェネレーター、NGen.exe によって生成された) 場合のイメージのベース アドレスは 0 になります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
