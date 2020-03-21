---
title: IMetaDataImport::GetPropertyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175331"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps メソッド
指定したトークンによって表されるプロパティのメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `prop`  
 [in]メタデータを返すプロパティを表すトークン。  
  
 `pClass`  
 [アウト]プロパティを実装する型を表す TypeDef トークンへのポインター。  
  
 `szProperty`  
 [アウト]プロパティ名を保持するバッファー。  
  
 `cchProperty`  
 [in]のワイド文字で表示される`szProperty`サイズ。  
  
 `pchProperty`  
 [アウト]に返されるワイド文字の`szProperty`数。  
  
 `pdwPropFlags`  
 [アウト]プロパティに適用される属性フラグへのポインター。 この値は[、CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)列挙体のビットマスクです。  
  
 `ppvSig`  
 [アウト]プロパティのメタデータ シグネチャへのポインター。  
  
 `pbSig`  
 [アウト]で返されるバイト数`ppvSig`。  
  
 `pdwCPlusTypeFlag`  
 [アウト]プロパティの既定値である定数の型を指定するフラグ。 この値は、CorElementType 列挙体から取得されます。  
  
 `ppDefaultValue`  
 [アウト]このプロパティの既定値を格納するバイトへのポインター。  
  
 `pcchDefaultValue`  
 [アウト]のワイド文字`ppDefaultValue`で示されるサイズ`pdwCPlusTypeFlag`は、ELEMENT_TYPE_STRING。それ以外の場合、この値は関係ありません。 その場合、の長`ppDefaultValue`さは で指定された型から推論されます。 `pdwCPlusTypeFlag`  
  
 `pmdSetter`  
 [アウト]プロパティの set アクセサー メソッドを表す MethodDef トークンへのポインター。  
  
 `pmdGetter`  
 [アウト]プロパティの get アクセサー メソッドを表す MethodDef トークンへのポインター。  
  
 `rmdOtherMethod`  
 [アウト]プロパティに関連付けられている他のメソッドを表す MethodDef トークンの配列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。 すべてのメソッドを保持するのに十分な大きさの配列を指定しない場合、警告なしにスキップされます。  
  
 `pcOtherMethod`  
 [アウト]に返される MethodDef トークン`rmdOtherMethod`の数。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
