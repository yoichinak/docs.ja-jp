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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 078dfd7162c250f0279b8bc372aeb39662aa0119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779887"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle メソッド
ICorDebugHeapValue2 オブジェクトによって表されるヒープ値の指定した型のハンドルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `type`  
 [in]CorDebugHandleType 列挙型を作成するハンドルの種類を指定する値。  
  
 `ppHandle`  
 [out]このヒープ値に対して新しいハンドルを表す ICorDebugHandleValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 ハンドルは、ヒープの値に関連付けられているアプリケーション ドメインでが作成され、アプリケーション ドメインがアンロードされると無効になります。  
  
 同じヒープ値に対してこの関数を複数の呼び出しでは、複数のハンドルを作成します。 ハンドルは、ガベージ コレクターのパフォーマンスに影響するために、一度にアクティブになっている (約 256) のハンドルの数を比較的小さなデバッガーに制限する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
