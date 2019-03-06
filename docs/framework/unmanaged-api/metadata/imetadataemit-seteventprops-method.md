---
title: IMetaDataEmit::SetEventProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1159e91004152b6c1393b87f25ff7964456adffc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498225"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps メソッド
前回の呼び出しで定義されたイベントの指定した機能の更新を設定または[imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ev`  
 [in]イベント トークンです。  
  
 `dwEventFlags`  
 [in]イベントのフラグ。 これは、ビットマスクの`CorEventAttr`値。  
  
 `tkEventType`  
 [in]イベント クラスのトークンです。 いずれかになります、`mdTypeDef`または`mdTypeRef`トークンです。  
  
 `mdAddOn`  
 [in]イベント、または null をサブスクライブするために使用するメソッド。  
  
 `mdRemoveOn`  
 [in]イベント、または null をアンサブスク ライブするメソッド。  
  
 `mdFire`  
 [in]イベントを発生させる (派生クラス) を使用するメソッド。  
  
 `rmdOtherMethods[]`  
 [in]イベントに関連付けられているその他のメソッドのトークンの配列。 配列の最後の要素である必要があります`mdMethodDefNil`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
