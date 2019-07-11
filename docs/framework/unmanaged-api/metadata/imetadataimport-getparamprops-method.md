---
title: IMetaDataImport::GetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9d2c74adecdfb0201f9f0c08998feba674f9e0f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778928"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps メソッド
指定した ParamDef トークンによって参照されるパラメーターのメタデータ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tk`  
 [in]メタデータを返すパラメーターを表す ParamDef トークンです。  
  
 `pmd`  
 [out]パラメーターを受け取るメソッドを表す MethodDef トークンへのポインター。  
  
 `pulSequence`  
 [out]メソッドの引数リストで、パラメーターの序数の位置。  
  
 `szName`  
 [out]パラメーターの名前を保持するバッファー。  
  
 `cchName`  
 [in]要求されたサイズのワイド文字単位`szName`します。  
  
 `pchName`  
 [out]ワイド文字で返されるサイズ`szName`します。  
  
 `pdwAttr`  
 [out]パラメーターに関連付けられているすべての属性フラグへのポインター。 これは、ビットマスクの`CorParamAttr`値。  
  
 `pdwCPlusTypeFlag`  
 [out]パラメーターを指定するフラグへのポインター、<xref:System.ValueType>します。  
  
 `ppValue`  
 [out]パラメーターによって返される定数文字列へのポインター。  
  
 `pcchValue`  
 [out]サイズ`ppValue`ワイド文字、または場合は 0 で`ppValue`文字列を保持しません。  
  
## <a name="remarks"></a>Remarks

シーケンスの値で`pulSequence`パラメーターの 1 から始まります。 戻り値は、シーケンス番号は 0 です。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
