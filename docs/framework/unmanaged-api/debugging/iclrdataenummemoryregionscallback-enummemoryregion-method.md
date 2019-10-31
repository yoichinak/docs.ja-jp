---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: 2ebe7ef37fb072e3688cc4dcfa5ed89832e886e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122932"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド
指定されたメモリ領域を列挙しようとした結果をデバッガーに報告するために、 [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)によって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 から列挙されたメモリ領域の開始アドレス。  
  
 `size`  
 からメモリ領域のサイズ (バイト単位)。  
  
## <a name="remarks"></a>Remarks  
 `ICLRDataEnumMemoryRegions::EnumMemoryRegions` メソッドは、メモリ領域を列挙するたびに、このコールバックメソッドを呼び出します。 このメソッドがエラーを示す HRESULT を返す場合でも、列挙は続行されます。  
  
 このコールバックによって報告されたリージョンが重複しているか、重複している可能性があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataEnumMemoryRegionsCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
