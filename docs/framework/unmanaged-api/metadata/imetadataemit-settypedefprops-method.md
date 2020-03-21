---
title: IMetaDataEmit::SetTypeDefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177463"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps メソッド
[:D 以前](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)の呼び出しで定義された型の機能を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]元`mdTypeDef`の呼び出しから取得したトークン[:D。](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`属性を指定します。 これは値の`CorTypeAttr`ビットマスクです。  
  
 `tkExtends`  
 [in]基本`mdToken`クラスの。 [:D 以前](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)の呼び出しから取得しました`null`。  
  
 `rtkImplements[]`  
 [in]この型が実装するインターフェイスのトークンの配列。 これらの`mdTypeRef`トークンは[、IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)を使用して取得されます。 配列の最後の要素は にする`mdTokenNil`必要があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
