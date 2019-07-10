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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8448de17ad974bc77021a7880b7d8576c69ae75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750916"
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps メソッド
前回の呼び出しで定義されているメソッドのパラメーターの機能の変更を設定または[imetadataemit::defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)します。  
  
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
 [in]ターゲットのパラメーターのトークンです。  
  
 `szName`  
 [in]Unicode でパラメーターの名前。  
  
 `dwParamFlags`  
 [in]パラメーターのフラグ。  
  
 `dwCPlusTypeFlag`  
 [in]ELEMENT_TYPE_ * 定数の値。  
  
 `pValue`  
 [in]パラメーターの定数値。  
  
 `cchValue`  
 [in] \(Unicode) 文字のサイズ`pValue`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
