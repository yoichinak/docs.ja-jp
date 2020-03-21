---
title: IMetaDataAssemblyImport::EnumAssemblyRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 6a4489d094974eb872b39824ceb185b0cbe48625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177826"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a>IMetaDataAssemblyImport::EnumAssemblyRefs メソッド
アセンブリ マニフェスト`mdAssemblyRef`で定義されているインスタンスを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [イン、アウト]列挙子へのポインター。 メソッドが初めて呼び出されたとき`EnumAssemblyRefs`は、この値は NULL 値である必要があります。  
  
 `rAssemblyRefs`  
 [アウト]メタデータ トークン`mdAssemblyRef`の列挙体。  
  
 `cMax`  
 [in]`rAssemblyRefs`配列に配置できるトークンの最大数。  
  
 `pcTokens`  
 [アウト]に実際に配置されたトークンの`rAssemblyRefs`数。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumAssemblyRefs`正常に返されました。|  
|`S_FALSE`|列挙するトークンがありません。 この場合、`pcTokens`ゼロに設定されます。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
