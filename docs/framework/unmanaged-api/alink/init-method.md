---
title: Init メソッド
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787249"
---
# <a name="init-method"></a>Init メソッド
使用する[Ialink インターフェイス](ialink-interface.md)を実装するオブジェクトを準備します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `pDispenser`  
 [IMetaDataDispenserEx インターフェイス](../metadata/imetadatadispenserex-interface.md)のメタデータディスペンサーへのポインター。  
  
 `pErrorHandler`  
 [IMetaDataError インターフェイス](../metadata/imetadataerror-interface.md)は、省略可能なエラー処理インターフェイスへのポインターです。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
