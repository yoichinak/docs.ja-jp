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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6c550ff7af2dda8bc06afd771024fe290339904
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089784"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps メソッド
指定したメタデータ シグネチャを持つアセンブリ参照のプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]`mdAssemblyRef`プロパティを取得する対象のアセンブリ参照を表すメタデータ トークン。  
  
 `ppbPublicKeyOrToken`  
 [out]公開キーまたはメタデータ トークンへのポインター。  
  
 `pcbPublicKeyOrToken`  
 [out]返される公開キー、またはトークンのバイト数。  
  
 `szName`  
 [out]アセンブリの簡易名。  
  
 `cchName`  
 [in]ワイド文字単位のサイズの`szName`します。  
  
 `pchName`  
 [out]実際に返されるワイド文字数へのポインター`szName`します。  
  
 `pMetaData`  
 [out]アセンブリのメタデータを含む ASSEMBLYMETADATA 構造体へのポインター。  
  
 `ppbHashValue`  
 [out]ハッシュ値へのポインター。 これは、sha-1 アルゴリズムを使用して、ハッシュ、 `PublicKey` 、arfFullOriginator のフラグを設定しない限り、参照されるアセンブリのプロパティ、 [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)列挙型を設定します。  
  
 `pcbHashValue`  
 [out]返されたハッシュ値のワイド文字の数。  
  
 `pdwAssemblyRefFlags`  
 [out]アセンブリに適用されるメタデータを記述するフラグをへのポインター。 フラグの値は、1 つ以上の組み合わせ[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)値。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、成功の場合は S_OK を返します。それ以外の場合、Winerror.h ヘッダー ファイルで定義されているエラー コードのいずれかを返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
