---
title: ICorPublishProcess::GetDisplayName メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6e7aa845f104ef734f039d46e1eeaba5fd01c73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221770"
---
# <a name="icorpublishprocessgetdisplayname-method"></a>ICorPublishProcess::GetDisplayName メソッド
これによって参照されるプロセスの実行可能ファイルの完全なパスを取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cchName`  
 [in] `szName` 配列のサイズ。  
  
 `pcchName`  
 [out]返されるワイド文字の数、`szName`配列。  
  
 `szName`  
 [out]実行可能ファイルの完全なパスを含む、名前を格納する配列。 名前では、null で終わります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublishProcess インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
