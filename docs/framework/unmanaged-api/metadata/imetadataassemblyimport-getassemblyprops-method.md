---
title: IMetaDataAssemblyImport::GetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177781"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps メソッド
指定したメタデータ シグネチャを持つアセンブリのプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mda`  
 [in]。 プロパティ`mdAssembly`を取得するアセンブリを表すメタデータ トークン。  
  
 `ppbPublicKey`  
 [アウト]公開キーまたはメタデータ トークンへのポインター。  
  
 `pcbPublicKey`  
 [アウト]返された公開キーのバイト数。  
  
 `pulHashAlgId`  
 [アウト]アセンブリ内のファイルをハッシュするために使用されるアルゴリズムへのポインター。  
  
 `szName`  
 [アウト]アセンブリの簡易名。  
  
 `cchName`  
 [in]のサイズ、ワイド文字で`szName`、 のサイズ。  
  
 `pchName`  
 [アウト]で実際に返されたワイド文字の`szName`数。  
  
 `pMetaData`  
 [アウト]アセンブリ メタデータを格納する ASSEMBLYMETADATA 構造体へのポインター。  
  
 `pdwAssemblyFlags`  
 [アウト]アセンブリに適用されるメタデータを記述するフラグ。 この値は、1 つ以上の[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)値の組み合わせです。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
