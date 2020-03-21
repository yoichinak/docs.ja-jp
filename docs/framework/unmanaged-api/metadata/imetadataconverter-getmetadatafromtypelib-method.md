---
title: IMetaDataConverter::GetMetaDataFromTypeLib メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: 09a1605deda5b51be604c3b8f0c69fa5adcf9dc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175955"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a>IMetaDataConverter::GetMetaDataFromTypeLib メソッド
指定したインスタンスによって表されるタイプ ライブラリのメタデータ シグネチャを表す[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)インスタンスへのインターフェイス`ITypeLib`ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pITL`  
 [in]タイプ ライブラリ`ITypeLib`を表すオブジェクトへのポインター。  
  
 `ppMDI`  
 [アウト]メタデータ シグネチャを表すインスタンスのアドレスを`IMetaDataImport`受け取る場所へのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
