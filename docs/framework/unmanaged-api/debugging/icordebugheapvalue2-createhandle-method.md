---
title: ICorDebugHeapValue2::CreateHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178882"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle メソッド
この ICorDebugHeapValue2 オブジェクトによって表されるヒープ値の指定された型のハンドルを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `type`  
 [in]作成するハンドルの型を指定する列挙体の値。  
  
 `ppHandle`  
 [アウト]このヒープ値の新しいハンドルを表すオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  
 ハンドルはヒープ値に関連付けられているアプリケーション ドメインに作成され、アプリケーション ドメインがアンロードされると無効になります。  
  
 同じヒープ値に対してこの関数を複数回呼び出すと、複数のハンドルが作成されます。 ハンドルはガベージ コレクターのパフォーマンスに影響するため、デバッガーは、一度にアクティブになっている比較的少数のハンドル (約 256) に限定する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
