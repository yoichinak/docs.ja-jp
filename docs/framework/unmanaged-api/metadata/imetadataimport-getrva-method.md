---
title: IMetaDataImport::GetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177213"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA メソッド
指定したトークンによって表されるメソッドまたはフィールドの相対仮想アドレス (RVA) および実装フラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tk`  
 [in]RVA を返すコード オブジェクトを表す MethodDef または FieldDef メタデータ トークン。 トークンが FieldDef の場合、フィールドはグローバル変数である必要があります。  
  
 `pulCodeRVA`  
 [アウト]トークンによって表されるコード オブジェクトの相対仮想アドレスへのポインター。  
  
 `pdwImplFlags`  
 [アウト]メソッドの実装フラグへのポインター。 この値は[、CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列挙型のビットマスクです。 の値`pdwImplFlags`は、MethodDef`tk`トークンの場合にのみ有効です。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
