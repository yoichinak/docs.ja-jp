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
ms.openlocfilehash: 3a05a779d4a56eb8f881da1824d5ffaa363b5a01
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274280"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration 関数
[列挙 Ateclrs 関数](enumerateclrs-function.md)によって返されるハンドルの配列にある有効な共通言語ランタイム (CLR) の継続スタートアップイベントをすべて閉じ、ハンドルおよび文字列パス配列のメモリを解放します。  
  
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
 から[列挙機能](enumerateclrs-function.md)から返されたイベントハンドルの配列へのポインター。  
  
 `pStringArray`  
 から[列挙型 Ateclrs 関数](enumerateclrs-function.md)から返された CLR 文字列パスの配列へのポインター。  
  
 `dwArrayLength`  
 [in] `pHandleArray` または `pStringArray` (これらは同じです) のサイズ (長さ) を含む DWORD。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 [列挙 Ateclrs 関数](enumerateclrs-function.md)によって開かれたハンドルが閉じられ、ハンドルおよび文字列配列に割り当てられたメモリが解放されます。  
  
 E_INVALIDARG  
 `pHandleArray` の長さが、`dwArrayLength` に渡された長さと一致しません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 `pHandleArray` および `pStringArray` のメモリを解放できません。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** dbgshim. h  
  
 **ライブラリ:** dbgshim .dll  
  
 **.NET Framework のバージョン:** 3.5 SP1
