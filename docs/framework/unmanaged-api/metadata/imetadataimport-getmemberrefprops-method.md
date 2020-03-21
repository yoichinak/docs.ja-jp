---
title: IMetaDataImport::GetMemberRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175370"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps メソッド
指定したトークンによって参照されるメンバーに関連付けられているメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,
   [out] mdToken           *ptk,
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pbSig
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mr`  
 [in]関連するメタデータを返す MemberRef トークン。  
  
 `ptk`  
 [アウト]メンバーを宣言するクラスを表す TypeDef または TypeRef トークン、またはメンバーを宣言するモジュール クラスを表す ModuleRef トークン、またはメンバーを表す MethodDef。  
  
 `szMember`  
 [アウト]メンバーの名前の文字列バッファー。  
  
 `cchMember`  
 [in]要求されたサイズは、 の`szMember`ワイド文字で表示されます。  
  
 `pchMember`  
 [アウト]返されるサイズは、 の`szMember`ワイド文字で表示されます。  
  
 `ppvSibBlob`  
 [アウト]メンバーのバイナリ メタデータ シグネチャへのポインター。  
  
 `pbSig`  
 [アウト]のサイズ (バイト`ppvSigBlob`単位)  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
