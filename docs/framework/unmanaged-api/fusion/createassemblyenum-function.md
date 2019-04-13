---
title: CreateAssemblyEnum 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0c5dabd4145098941e9e8a7e36fa3215c26713d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084921"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum 関数
ポインターを取得、 [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)インスタンスの指定したアセンブリ内のオブジェクトを列挙できる[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>パラメーター  
 `pEnum`  
 [out]含む、要求されたメモリ位置へのポインター`IAssemblyEnum`ポインター。  
  
 `pUnkReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pUnkReserved` null 参照である必要があります。  
  
 `pName`  
 [in]`IAssemblyName`の要求されたアセンブリ。 この名前は、列挙型をフィルター処理に使用されます。 グローバル アセンブリ キャッシュ内のすべてのアセンブリを列挙する場合は null になります。  
  
 `dwFlags`  
 [in]列挙子の動作を変更するためのフラグ。 このパラメーターには正確に 1 ビットが含まれています、 [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)列挙体。  
  
 `pvReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pvReserved` null 参照である必要があります。  
  
## <a name="remarks"></a>Remarks  
 `dwFlags`パラメーターにはから厳密に 1 ビットが含まれています、`ASM_CACHE_FLAGS`列挙体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [IAssemblyName インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
