---
title: CloseCLREnumeration 関数
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9eb9bb1e4abeb98d8d0ba2b052612d918c45f22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741087"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration 関数
有効な共通言語ランタイム (CLR) 継続スタートアップ イベントによって返されるハンドルの配列内にあるを閉じ、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)、ハンドルおよび文字列パス配列のメモリを解放します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pHandleArray`  
 [in]返されたイベント ハンドルの配列へのポインター、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)します。  
  
 `pStringArray`  
 [in]返される CLR 文字列パスの配列へのポインター、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)します。  
  
 `dwArrayLength`  
 [in] `pHandleArray` または `pStringArray` (これらは同じです) のサイズ (長さ) を含む DWORD。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 によって開かれたハンドル、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)が終了し、ハンドルおよび文字列の配列に割り当てられたメモリを解放します。  
  
 E_INVALIDARG  
 `pHandleArray` の長さが、`dwArrayLength` に渡された長さと一致しません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 `pHandleArray` および `pStringArray` のメモリを解放できません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** dbgshim.h  
  
 **ライブラリ:** dbgshim.dll  
  
 **.NET framework のバージョン:** 3.5 SP1
