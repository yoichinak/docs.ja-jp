---
title: ICorDebugMergedAssemblyRecord::GetSimpleName メソッド
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0914c09fbbef5efb64fb253a4ea36d5b6c97ba97
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479104"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergedAssemblyRecord::GetSimpleName メソッド
アセンブリの簡易名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cchName`  
 [in] `szName` バッファー内の文字数。  
  
 `pcchName`  
 [out] `szName` バッファーに実際に書き込まれた文字数へのポインター。  
  
 `szName`  
 文字配列へのポインター。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、アセンブリの簡易名 ("System.Collections" など) を取得します。簡易名には、ファイル拡張子、バージョン、カルチャ、公開キー トークンが含まれていません。 これはマネージ コード内の <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> プロパティに対応します。  
  
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
