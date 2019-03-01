---
title: CoUninitializeCor 関数
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dca4fd4a4d20627bef8f7fedd5a801ba07e8e19b
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212080"
---
# <a name="couninitializecor-function"></a>CoUninitializeCor 関数
`CoUninitializeCor` は互換性のために残されています。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイムは、プロセスからアンロードすることはできません。 実行中のプロセスからランタイムを完全に削除するには、そのプロセスをシャット ダウンする必要があります。  
  
## <a name="see-also"></a>関連項目
- [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
