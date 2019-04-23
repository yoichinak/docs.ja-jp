---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken メソッド
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a4a8e5f99a845d2befe55f5939b41224f2aa47b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077304"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKeyToken メソッド
アセンブリの公開キー トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cbPublicKeyToken`  
 [in] `pbPublicKeyToken` 配列の最大バイト数。  
  
 `pcbPublicKeyToken`  
 [out] `pbPublicKeyToken` 配列への実際の書き込みバイト数へのポインター。  
  
 `pbPublicKeyToken`  
 [out] アセンブリの公開キー トークンを含むバイト配列へのポインター。  
  
## <a name="remarks"></a>Remarks  
 アセンブリの公開キー トークンは、その公開キーの SHA1 ハッシュの最後の 8 バイトです。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMergedAssemblyRecord インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
