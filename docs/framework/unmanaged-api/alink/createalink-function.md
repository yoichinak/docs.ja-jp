---
title: CreateALink 関数
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11117db08d58684cc854400424d1836ec35b8c12
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498010"
---
# <a name="createalink-function"></a>CreateALink 関数
アセンブリ リンカーのインスタンスを作成し、指定したインターフェイスへのポインターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`riid`|アセンブリ リンカー インターフェイスの 1 つの物理名。|  
|`ppInterface`|正常に完了へのポインターを格納する場所、`riid`インターフェイス。|  
  
## <a name="requirements"></a>必要条件  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目
- [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
