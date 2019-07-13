---
title: ICorDebugEval::NewArray メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9597d05e46c2d41ab1f24a073c028561e944fb59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753032"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray メソッド
指定した要素型とディメンションの新しい配列を割り当てます。  
  
 このメソッドは、.NET Framework version 2.0 で廃止されています。 使用[icordebugeval 2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)代わりにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]CorElementType 列挙型、配列の要素の型を指定する値。  
  
 `pElementClass`  
 [in]要素のクラスを指定する ICorDebugClass オブジェクトへのポインター。 この値を要素の型がプリミティブ型の場合は null にすることがあります。  
  
 `rank`  
 [in]配列の次元の数。 .NET Framework 2.0 でこの値は 1 にある必要があります。  
  
 `dims`  
 [in]配列の各次元のバイト単位のサイズ。  
  
 `lowBounds`  
 [in] オプション。 配列の各次元の下限値です。 この値を省略すると、各ディメンションの下限を 0 が使われます。  
  
## <a name="remarks"></a>Remarks  
 配列が常に現在のスレッドが実行されているアプリケーション ドメインで作成されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1, 1.0
