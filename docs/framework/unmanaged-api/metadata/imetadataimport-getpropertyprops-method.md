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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e83afcf6c872927e614fce33ca96e93f0da4f497
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778876"
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
 [in]メタデータを返すプロパティを表すトークンです。  
  
 `pClass`  
 [out]プロパティを実装する型を表す TypeDef トークンへのポインター。  
  
 `szProperty`  
 [out]プロパティ名を保持するバッファー。  
  
 `cchProperty`  
 [in]ワイド文字単位サイズ`szProperty`します。  
  
 `pchProperty`  
 [out]返されるワイド文字数`szProperty`します。  
  
 `pdwPropFlags`  
 [out]プロパティに適用される属性フラグのいずれかへのポインター。 この値はビットマスクから、 [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)列挙体。  
  
 `ppvSig`  
 [out]プロパティのメタデータ署名へのポインター。  
  
 `pbSig`  
 [out]返されるバイト数`ppvSig`します。  
  
 `pdwCPlusTypeFlag`  
 [out]プロパティの既定値である定数の型を指定するフラグ。 この値は CorElementType 列挙型です。  
  
 `ppDefaultValue`  
 [out]このプロパティの既定値を格納するバイト数へのポインター。  
  
 `pcchDefaultValue`  
 [out]ワイド文字単位サイズ`ppDefaultValue`場合は、 `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING; は、それ以外の場合、この値は関連はありません。 その場合、長さの`ppDefaultValue`によって指定された型から推論されます`pdwCPlusTypeFlag`します。  
  
 `pmdSetter`  
 [out]プロパティの set アクセサー メソッドを表す MethodDef トークンへのポインター。  
  
 `pmdGetter`  
 [out]プロパティの get アクセサー メソッドを表す MethodDef トークンへのポインター。  
  
 `rmdOtherMethod`  
 [out]プロパティに関連付けられているその他のメソッドを表す MethodDef トークンの配列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。 すべてのメソッドを保持するために十分な大きさの配列を指定しない場合は警告なしスキップされます。  
  
 `pcOtherMethod`  
 [out]返される MethodDef トークン数`rmdOtherMethod`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
