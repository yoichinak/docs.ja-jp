---
title: ICorDebugModule::GetMetaDataInterface メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37710fbb7acc50b80d7acebe4194b019c0b64660
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102597"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface メソッド
モジュールのメタデータの検査に使用できるメタデータ インターフェイス オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `riid`  
 [in]メタデータ インターフェイスを指定する参照の ID です。  
  
 `ppObj`  
 [out]アドレスへのポインター、`T:IUnknown`のいずれかであるオブジェクトを[メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)します。  
  
## <a name="remarks"></a>Remarks  
 デバッガーを使用できる、 `GetMetaDataInterface` 、モジュールのモジュールを編集するにはこれを行う必要がありますが、元のメタデータのコピーを作成するメソッド。 デバッガーの呼び出し`GetMetaDataInterface`を取得する、 [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)インターフェイス オブジェクト、モジュールの呼び出し、 [imetadataemit::savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)モジュールのメタデータのコピーをメモリに保存します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ](../../../../docs/framework/unmanaged-api/metadata/index.md)
