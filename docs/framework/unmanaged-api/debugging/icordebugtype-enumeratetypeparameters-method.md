---
title: ICorDebugType::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8fa39a54437e60737aa052c495f58422bc0d3fe
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474450"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters メソッド
含む、ICorDebugTypeEnum インターフェイス ポインターを取得、<xref:System.Type>この ICorDebugType によって参照されるクラスのパラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppTyParEnum`  
 [out]アドレスへのポインター、`ICorDebugTypeEnum`型のパラメーターを格納しています。  
  
## <a name="remarks"></a>Remarks  
 使用することができます`EnumerateTypeParameters`CorElementType 値がによって返される場合[icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS、ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、ELEMENT_TYPE_PTR、または typ ELEMENT_TYPE_FNPTR します。 パラメーターとその順序の数は、種類によって異なります。  
  
-   ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE:含まれる型パラメーターの数、`ICorDebugTypeEnum`このメソッドが返すし、対応するクラスの仮引数の型パラメーターの数によって異なります。 たとえば、次の種類は`class Dict<String,int32>`、し`EnumerateTypeParameters`が返されます、`ICorDebugTypeEnum`を表すオブジェクトを格納している`String`と`int32`シーケンスでします。  
  
-   TYP ELEMENT_TYPE_FNPTR:含まれる型パラメーターの数、`ICorDebugTypeEnum`はいずれかに、関数が受け取る引数の数を超えています。 含まれる最初の型パラメーター、`ICorDebugTypeEnum`関数の戻り値の型であり、その後の型パラメーターは関数のパラメーター。  
  
-   ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR:1 つの型パラメーターが返されます。 たとえば、型が配列型などに設定されている場合`int32[]`、`EnumerateTypeParameters`が返されます、`ICorDebugTypeEnum`表すオブジェクトを格納している`int32`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
