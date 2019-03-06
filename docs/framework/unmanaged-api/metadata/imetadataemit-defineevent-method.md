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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 26fd4c89838912e4e07c1d9a8b84aa22f54adeff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501631"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent メソッド
指定したメタデータ シグネチャを持つイベントの定義を作成し、そのイベント定義トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]ターゲット クラスまたはインターフェイスのトークンです。 いずれかになります、`mdTypeDef`または`mdTypeDefNil`トークンです。  
  
 `szEvent`  
 [in]イベントの名前。  
  
 `dwEventFlags`  
 [in]イベントのフラグ。  
  
 `tkEventType`  
 [in]イベント クラスのトークンです。 これは、 `mdTypeDef`、 `mdTypeRef`、または`mdTokenNil`トークンです。  
  
 `mdAddOn`  
 [in]イベント、または null をサブスクライブするために使用するメソッド。  
  
 `mdRemoveOn`  
 [in]イベント、または null をアンサブスク ライブするメソッド。  
  
 `mdFire`  
 [in]イベントを発生させる (派生クラス) を使用するメソッド。  
  
 `rmdOtherMethods[]`  
 [in]イベントに関連付けられているその他のメソッドのトークンの配列。 配列が終了しました、`mdMethodDefNil`トークンです。  
  
 `pmdEvent`  
 [out]イベントに割り当てられているメタデータ トークンです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
