---
title: IMetaDataAssemblyImport::GetExportedTypeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177759"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps メソッド
指定したメタデータ シグネチャを持つエクスポートされた型のプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mdct`  
 [in]エクスポート`mdExportedType`された型を表すメタデータ トークン。  
  
 `szName`  
 [アウト]エクスポートされた型の名前。  
  
 `cchName`  
 [in]のサイズ (ワイド文字)`szName`です。  
  
 `pchName`  
 [アウト]実際に返されるワイド文字の数`szName`  
  
 `ptkImplementation`  
 [アウト]エクスポート`mdFile`された`mdAssemblyRef`型の`mdExportedType`プロパティを格納または許可する 、または、エクスポートされた型のプロパティへのアクセスを許可する 、、、、またはメタデータ トークン。  
  
 `ptkTypeDef`  
 [アウト]ファイル内の型`mdTypeDef`を表すトークンへのポインター。  
  
 `pdwExportedTypeFlags`  
 [アウト]エクスポートされた型に適用されるメタデータを記述するフラグへのポインター。 フラグ値は、1 つまたは複数[の CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)値にすることができます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
