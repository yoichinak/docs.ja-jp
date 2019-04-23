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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96c013cd3e45e4ede0cbc9f42bf511a2eb3fc12d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223590"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA メソッド
相対仮想アドレス (RVA) と、メソッド、または指定したトークンによって表されるフィールドの実装フラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tk`  
 [in]RVA を返すコード オブジェクトを表す MethodDef または FieldDef メタデータ トークン。 トークンが、FieldDef の場合は、フィールドは、グローバル変数である必要があります。  
  
 `pulCodeRVA`  
 [out]トークンが表すコード オブジェクトの相対仮想アドレスへのポインター。  
  
 `pdwImplFlags`  
 [out]メソッドの実装フラグへのポインター。 この値はビットマスクから、 [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列挙体。 値`pdwImplFlags`は有効な場合にのみ`tk`MethodDef トークンです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
