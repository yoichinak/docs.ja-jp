---
title: IMetaDataEmit::SetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177569"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout メソッド
[DefineTypeDef メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)の前の呼び出しによって定義されたクラスのフィールドのレイアウトを完了します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]レイアウト`mdTypeDef`するクラスを指定するトークン。  
  
 `dwPackSize`  
 [in]パッキング サイズ: 1、2、4、8 または 16 バイト。 パッキング・サイズは、隣接するフィールド間のバイト数です。  
  
 `rFieldOffsets`  
 [in]COR_FIELD_OFFSET[構造体の](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)配列で、各構造体はクラスのフィールドとクラス内のフィールドのオフセットを指定します。 配列を`mdTokenNil`で終了します。  
  
 `ulClassSize`  
 [in]クラスのサイズ (バイト単位)。  
  
## <a name="remarks"></a>解説  
 このクラスは、最初は[IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)メソッドを呼び出し、クラスのフィールドに対して自動、順次、または明示的な 3 つのレイアウトのいずれかを指定することによって定義されます。 通常は自動レイアウトを使用し、実行時にフィールドをレイアウトする最適な方法を選択します。  
  
 ただし、アンマネージ コードで使用される配置に従ってフィールドをレイアウトする場合があります。 この場合は、シーケンシャルレイアウトまたは明示的レイアウトを`SetClassLayout`選択し、フィールドのレイアウトを完了するために呼び出します。  
  
- シーケンシャルレイアウト: 梱包サイズを指定します。 フィールドは、自然なサイズまたはパッキング サイズのいずれかに従って配置されます。 0 `rFieldOffsets` `ulClassSize`に設定します。  
  
- 明示的なレイアウト: 各フィールドのオフセットを指定するか、クラスサイズとパッキングサイズを指定します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
