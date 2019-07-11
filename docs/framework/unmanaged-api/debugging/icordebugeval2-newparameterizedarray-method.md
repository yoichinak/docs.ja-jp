---
title: ICorDebugEval2::NewParameterizedArray メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 973f975885bbbf5cbed74adef7b9f4f423c42583
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753657"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray メソッド
指定した要素型とディメンションの新しい配列を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pElementType`  
 [in]配列に格納されている要素の型を表す ICorDebugType オブジェクトへのポインター。  
  
 `rank`  
 [in]配列の次元の数。 .NET framework version 2.0 では、この値は 1 にある必要があります。  
  
 `dims`  
 [in]配列の各次元のバイト単位のサイズ。  
  
 `lowBounds`  
 [in] オプション。 配列の各次元の下限値です。 この値を省略すると、各ディメンションの下限を 0 が使われます。  
  
## <a name="remarks"></a>Remarks  
 配列の要素には、ジェネリック型のインスタンスを使用できます。 配列が常に、スレッドが現在実行されているアプリケーション ドメインで作成されます。 .NET Framework 2.0 の値で`rank`1 である必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
