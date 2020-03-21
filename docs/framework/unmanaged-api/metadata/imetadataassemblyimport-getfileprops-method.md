---
title: IMetaDataAssemblyImport::GetFileProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175981"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps メソッド
指定したメタデータ シグネチャを持つファイルのプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mdf`  
 [in]プロパティ`mdFile`を取得する対象のファイルを表すメタデータ トークン。  
  
 `szName`  
 [アウト]ファイルの簡易名。  
  
 `cchName`  
 [in]のサイズ、ワイド文字で`szName`、 のサイズ。  
  
 `pchName`  
 [アウト]で実際に返されたワイド文字の`szName`数。  
  
 `ppbHashValue`  
 [アウト]ハッシュ値へのポインター。 これは、SHA-1 アルゴリズムを使用したファイルのハッシュです。  
  
 `pcbHashValue`  
 [アウト]返されたハッシュ値のワイド文字の数。  
  
 `pdwFileFlags`  
 [アウト]ファイルに適用されるメタデータを記述するフラグへのポインター。 フラグ値は、1 つ以上の[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)値の組み合わせです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
