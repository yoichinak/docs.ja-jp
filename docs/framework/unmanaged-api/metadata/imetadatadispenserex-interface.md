---
title: IMetaDataDispenserEx インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431144"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx インターフェイス
Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FindAssembly メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|このメソッドは実装されていません。 If called, it returns E_NOTIMPL.|  
|[FindAssemblyModule メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|このメソッドは実装されていません。 If called, it returns E_NOTIMPL.|  
|[GetCORSystemDirectory メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Gets the directory that holds the current common language runtime (CLR). This method is supported only for use by out-of-process debuggers. If called from another component, it will return E_NOTIMPL.|  
|[GetOption メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Gets the value of the specified option for the current metadata scope. The option controls how calls to the current metadata scope are handled.|  
|[OpenScopeOnITypeInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|このメソッドは実装されていません。 If called, it returns E_NOTIMPL.|  
|[SetOption メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Sets the specified option to a given value for the current metadata scope. The option controls how calls to the current metadata scope are handled.|  
  
## <a name="requirements"></a>［要件］  
 **Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
