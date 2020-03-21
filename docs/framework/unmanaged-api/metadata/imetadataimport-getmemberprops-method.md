---
title: IMetaDataImport::GetMemberProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177230"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps メソッド
指定したメタデータ トークンによって参照されるメンバーの名前、バイナリ シグネチャ、相対仮想アドレスなど、指定した<xref:System.Type>メンバー定義のメタデータに格納されている情報を取得します。 これは単純なヘルパー メソッドです: *mb*がメソッド定義の場合は **、GetMethodProps**が呼び出されます。*mb*がフィールド定義の場合は **、GetFieldProps が**呼び出されます。 詳細については、他の方法を参照してください。
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mb`  
 [in]関連付けられたメタデータを取得するメンバーを参照するトークン。  
  
 `pClass`  
 [アウト]メンバーのクラスを表すメタデータ トークンへのポインター。  
  
 `szMember`  
 [アウト]メンバーの名前。  
  
 `cchMember`  
 [in]バッファーのワイド文字で示される`szMember`サイズ。  
  
 `pchMember`  
 [アウト]返された名前のワイド文字で示されるサイズ。  
  
 `pdwAttr`  
 [アウト]メンバーに適用されるフラグ値。  
  
 `ppvSigBlob`  
 [アウト]メンバーのバイナリ メタデータ シグネチャへのポインター。  
  
 `pcbSigBlob`  
 [アウト]のサイズ (バイト`ppvSigBlob`単位)  
  
 `pulCodeRVA`  
 [アウト]メンバーの相対仮想アドレスへのポインター。  
  
 `pdwImplFlags`  
 [アウト]メンバーに関連付けられたメソッド実装フラグ。  
  
 `pdwCPlusTypeFlag`  
 [アウト]をマークするフラグ。 <xref:System.ValueType> これは値の`ELEMENT_TYPE_*`1 つです。
  
 `ppValue`  
 [アウト]このメンバーによって返される定数文字列値。  
  
 `pcchValue`  
 [アウト]のサイズを文字`ppValue`で指定`ppValue`します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
