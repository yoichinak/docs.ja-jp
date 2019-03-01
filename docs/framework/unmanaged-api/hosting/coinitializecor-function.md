---
title: CoInitializeCor 関数
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 556d26ac7e4fb8847f132d19bd2e749aff345abf
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211846"
---
# <a name="coinitializecor-function"></a>CoInitializeCor 関数
`CoInitializeCor` は互換性のために残されています。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイムを初期化するためにいずれかの操作を使用して[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)または[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** Cor.h  
  
## <a name="see-also"></a>関連項目
- [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
