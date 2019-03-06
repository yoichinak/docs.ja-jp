---
title: ICorDebugAppDomain2::GetArrayOrPointerType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58a39771bd89fc9c4947f80a3c87b4d340b5461c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484239"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType メソッド
指定した型、ポインター、または指定した型への参照の配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]CorElementType 列挙型 (配列、ポインター、または参照) を作成する基になるネイティブな型を指定する値。  
  
 `nRank`  
 [in]配列のランク (つまり、ディメンションの数)。 場合、この値は 0 には`elementType`ポインターまたは参照型を指定します。  
  
 `pTypeArg`  
 [in]配列の型を表す ICorDebugType オブジェクトへのポインター、ポインター、または参照を作成します。  
  
 `ppType`  
 [out]アドレスへのポインター、`ICorDebugType`構築された配列、ポインター型、または参照を表すオブジェクトを入力します。  
  
## <a name="remarks"></a>Remarks  
 値*elementType*次のいずれかを指定する必要があります。  
  
-   ELEMENT_TYPE_PTR  
  
-   ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY または ELEMENT_TYPE_SZARRAY  
  
 場合の値*elementType* ELEMENT_TYPE_PTR または ELEMENT_TYPE_BYREF、 *nRank* 0 にする必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
