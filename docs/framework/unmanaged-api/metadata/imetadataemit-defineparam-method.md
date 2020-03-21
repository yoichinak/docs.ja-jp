---
title: IMetaDataEmit::DefineParam メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177695"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam メソッド
指定したトークンによって参照されるメソッドの指定したシグネチャを持つパラメーター定義を作成し、そのパラメーター定義のトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `md`  
 [in]パラメーターが定義されているメソッドのトークン。  
  
 `ulParamSeq`  
 [in]パラメーターのシーケンス番号。  
  
 `szName`  
 [in]ユニコードのパラメータの名前。  
  
 `dwParamFlags`  
 [in]パラメーターのフラグ。 これは値の`CorParamAttr`ビットマスクです。  
  
 `dwCPlusTypeFlag`  
 [in]`ELEMENT_TYPE_`を定数値に対して指定*\** します。  
  
 `pValue`  
 [in]パラメーターの定数値。  
  
 `cchValue`  
 [in]のサイズ (Unicode 文字) `pValue`  
  
 `ppd`  
 [アウト]割`mdParamDef`り当てられたトークン。  
  
## <a name="remarks"></a>解説  
 シーケンス値は、`ulParamSeq`パラメーターの場合は 1 から始まります。 戻り値のシーケンス番号は 0 です。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
