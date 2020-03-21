---
title: IMetaDataAssemblyImport::GetAssemblyRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175968"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps メソッド
指定したメタデータ シグネチャを持つアセンブリ参照のプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mdar`  
 [in]プロパティ`mdAssemblyRef`を取得するアセンブリ参照を表すメタデータ トークン。  
  
 `ppbPublicKeyOrToken`  
 [アウト]公開キーまたはメタデータ トークンへのポインター。  
  
 `pcbPublicKeyOrToken`  
 [アウト]返された公開キーまたはトークンのバイト数。  
  
 `szName`  
 [アウト]アセンブリの簡易名。  
  
 `cchName`  
 [in]のサイズ、ワイド文字で`szName`、 のサイズ。  
  
 `pchName`  
 [アウト]で実際に返されるワイド文字の数へのポインタ`szName`。  
  
 `pMetaData`  
 [アウト]アセンブリ メタデータを格納する ASSEMBLYMETADATA 構造体へのポインター。  
  
 `ppbHashValue`  
 [アウト]ハッシュ値へのポインター。 これは、`PublicKey`[参照](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)されるアセンブリのプロパティの SHA-1 アルゴリズムを使用するハッシュです。  
  
 `pcbHashValue`  
 [アウト]返されたハッシュ値のワイド文字の数。  
  
 `pdwAssemblyRefFlags`  
 [アウト]アセンブリに適用されるメタデータを記述するフラグへのポインター。 フラグ値は、1 つまたは複数の[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)値の組み合わせです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、成功した場合はS_OKを返します。それ以外の場合は、Winerror.h ヘッダー ファイルで定義されているエラー コードのいずれかを返します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
