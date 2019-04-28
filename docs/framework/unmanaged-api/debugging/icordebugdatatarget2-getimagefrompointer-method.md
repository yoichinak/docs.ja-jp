---
title: ICorDebugDataTarget2::GetImageFromPointer メソッド
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dab9183075f563f52a4fc982eda5cb172556554
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782981"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a>ICorDebugDataTarget2::GetImageFromPointer メソッド
モジュールのアドレスから、そのモジュールのベース アドレスとサイズを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `addr`  
 A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)モジュール内のアドレスを表す値です。  
  
 `pImageBase`  
 [out]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)モジュールのベース アドレスを表す値です。  
  
 `pSize`  
 モジュールのサイズへのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
