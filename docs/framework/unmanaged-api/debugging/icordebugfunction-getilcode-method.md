---
title: ICorDebugFunction::GetILCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f34a2fe2bb1f92e75f77c086b03776ec59495600
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995749"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode メソッド
この ICorDebugFunction オブジェクトに関連付けられている Microsoft intermediate language (MSIL) コードを表す ICorDebugCode インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppCode`  
 [out]ポインター、`ICorDebugCode`インスタンス、または関数が MSIL にコンパイルされていない場合は null です。  
  
## <a name="remarks"></a>Remarks  
 この関数では、エディット コンティニュが許可されている場合、`GetILCode`メソッドが共通言語ランタイム (CLR) 内のコードのこの関数の編集済みのバージョンに対応する MSIL コードを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
