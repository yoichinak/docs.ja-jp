---
title: IMetaDataEmit::DefineTypeRefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 23a6931b31ea2d7e4e8d1cb3dc8adf3a51216315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175747"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName メソッド
現在のスコープの外側にある、指定したスコープで定義されている型のメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkResolutionScope`  
 [in]解決スコープを指定するトークン。 次のトークンタイプが有効です。  
  
- `mdModuleRef`型が、呼び出し元が定義されているアセンブリと同じアセンブリで定義されている場合。  
  
- `mdAssemblyRef`型が、呼び出し元が定義されているアセンブリ以外のアセンブリで定義されている場合。  
  
- `mdTypeRef`の場合、その型が入れ子にされた型です。  
  
- `mdModule`型が、呼び出し元が定義されているモジュールと同じモジュールで定義されている場合。  
  
- 型がグローバルに定義されている場合は Null。  
  
 `szName`  
 [in]ユニコードでのターゲット型の名前。  
  
 `ptr`  
 [アウト]型に割り`mdTypeRef`当てられているトークンへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
