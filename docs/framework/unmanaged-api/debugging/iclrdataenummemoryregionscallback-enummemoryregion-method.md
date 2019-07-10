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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5c03b7010418f75aff984102d7fa4fb089c4d59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738825"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion メソッド
によって呼び出される[iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)メモリの指定した領域の列挙の試行の結果をデバッガーに報告します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in]列挙されるメモリ領域の開始アドレス。  
  
 `size`  
 [in] \(バイト単位\) のメモリ領域のサイズ。  
  
## <a name="remarks"></a>コメント  
 `ICLRDataEnumMemoryRegions::EnumMemoryRegions`メソッドは、メモリ領域を列挙するために試行するたびにこのコールバック メソッドを呼び出します。 このメソッドは、エラーを示す HRESULT を返した場合であっても、列挙は継続されます。  
  
 このコールバックによって報告されたリージョンには、重複またはオーバー ラップがあります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataEnumMemoryRegionsCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
