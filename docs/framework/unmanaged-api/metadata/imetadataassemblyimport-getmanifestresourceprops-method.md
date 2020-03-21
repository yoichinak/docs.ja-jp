---
title: IMetaDataAssemblyImport::GetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177653"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps メソッド
指定したメタデータ シグネチャを持つマニフェスト リソースのプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mdmr`  
 [in]プロパティ`mdManifestResource`を取得するリソースを表すトークン。  
  
 `szName`  
 [アウト]リソースの名前。  
  
 `cchName`  
 [in]のサイズ、ワイド文字で`szName`、 のサイズ。  
  
 `pchName`  
 [アウト]で実際に返されるワイド文字の数へのポインタ`szName`。  
  
 `ptkImplementation`  
 [アウト]リソースを`mdFile`含むファイルまたはアセンブリ`mdAssemblyRef`を表すトークンまたはトークンへのポインター。  
  
 `pdwOffset`  
 [アウト]ファイル内のリソースの先頭へのオフセットを指定する値へのポインター。  
  
 `pdwResourceFlags`  
 [アウト]リソースに適用されるメタデータを記述するフラグへのポインター。 フラグ値は、1 つ以上の[CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)値の組み合わせです。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
