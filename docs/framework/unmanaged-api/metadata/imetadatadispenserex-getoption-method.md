---
title: IMetaDataDispenserEx::GetOption メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177726"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption メソッド
現在のメタデータ スコープの指定されたオプションの値を取得します。 このオプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `optionId`  
 [in]取得するオプションを指定する GUID へのポインター。 サポートされている GUID の一覧については、「解説」を参照してください。  
  
 `pValue`  
 [アウト]返されるオプションの値。 この値の型は、指定されたオプションの型のバリアントになります。  
  
## <a name="remarks"></a>解説  
 このメソッドでサポートされている GUID を次に示します。 詳細については[、メソッドを](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)参照してください。 この`optionId`リストに含まれていない場合、このメソッドは、誤`E_INVALIDARG`ったパラメーターを示す HRESULT を返します。  
  
- メタデータチェック重複  
  
- をチェックします。  
  
- トークンの動き  
  
- メタデータセットエンク  
  
- 注文のエラーをエラーします。  
  
- メタデータ生成TCEアダプター  
  
- メタデータリンカーのオプション  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
