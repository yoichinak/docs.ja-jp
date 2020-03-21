---
title: IMetaDataEmit::SetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177506"
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps メソッド
[IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)への以前の呼び出しによって定義されたメソッド パラメーターの機能を設定または変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pd`  
 [in]ターゲット パラメーターのトークン。  
  
 `szName`  
 [in]ユニコードのパラメータの名前。  
  
 `dwParamFlags`  
 [in]パラメーターのフラグ。  
  
 `dwCPlusTypeFlag`  
 [in]定数値のELEMENT_TYPE_* です。  
  
 `pValue`  
 [in]パラメーターの定数値。  
  
 `cchValue`  
 [in]のサイズ (Unicode) 文字`pValue`  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
