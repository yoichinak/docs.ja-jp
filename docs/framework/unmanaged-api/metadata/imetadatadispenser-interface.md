---
title: IMetaDataDispenser インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: b7ce76c22e7188117bddd9e4f328e323f6742685
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436227"
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser インターフェイス
Provides methods to create a new metadata scope, or open an existing one.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DefineScope メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|Creates a new area in memory where you can create new metadata.|  
|[OpenScope メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|Opens an existing, on-disk file and maps its metadata into memory.|  
|[OpenScopeOnMemory メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|Opens an area of memory that contains existing metadata. That is, this method opens a specified area of memory in which the existing data is treated as metadata.|  
  
## <a name="requirements"></a>［要件］  
 **Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
