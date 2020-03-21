---
title: IMetaDataEmit::DefineEvent メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175851"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent メソッド
指定したメタデータ シグネチャを持つイベントの定義を作成し、そのイベント定義へのトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]ターゲット クラスまたはインターフェイスのトークン。 これは、`mdTypeDef`トークンまたは`mdTypeDefNil`トークンです。  
  
 `szEvent`  
 [in]イベントの名前。  
  
 `dwEventFlags`  
 [in]イベント フラグ。  
  
 `tkEventType`  
 [in]イベント クラスのトークン。 これは`mdTypeDef`、 、または`mdTypeRef`トークンです`mdTokenNil`。  
  
 `mdAddOn`  
 [in]イベントをサブスクライブするために使用するメソッド、または null。  
  
 `mdRemoveOn`  
 [in]イベントのサブスクライブを解除するために使用するメソッド、または null。  
  
 `mdFire`  
 [in]イベントを発生させるために (派生クラスによって) 使用されるメソッド。  
  
 `rmdOtherMethods[]`  
 [in]イベントに関連付けられている他のメソッドのトークンの配列。 配列は`mdMethodDefNil`トークンで終了します。  
  
 `pmdEvent`  
 [アウト]イベントに割り当てられたメタデータ トークン。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
