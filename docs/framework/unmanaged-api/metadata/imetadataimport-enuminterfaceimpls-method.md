---
title: IMetaDataImport::EnumInterfaceImpls メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21d70b2702a754b554f06de5dad776ae98ae918d
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836267"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls メソッド
指定したによって実装されるすべてのインターフェイスを列挙`TypeDef`します。 
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力]列挙子へのポインター。  
  
 `td`  
 [in]インターフェイスの実装を表す MethodDef トークンを持つが列挙 TypeDef のトークンです。  
  
 `rImpls`  
 [out]MethodDef トークンを格納するために使用する配列。  
  
 `cMax`  
 [in] `rImpls` 配列の最大サイズ。  
  
 `pcImpls`  
 [out]実際のトークンで返される数`rImpls`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` 正常に返されます。|  
|`S_FALSE`|MethodDef トークンを列挙することはありません。 その場合は、 `pcImpls` 0 に設定されます。|  

## <a name="remarks"></a>Remarks

列挙体のコレクションを返します`mdInterfaceImpl`各インターフェイスを指定した実装のためのトークン`TypeDef`します。 インターフェイスのトークンは、インターフェイスが指定された順序で返されます (を通じて`DefineTypeDef`または`SetTypeDefProps`)。 プロパティは、返された`mdInterfaceImpl`を使用してトークンを照会できます[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)します。
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
