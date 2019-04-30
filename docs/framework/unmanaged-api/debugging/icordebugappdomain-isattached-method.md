---
title: ICorDebugAppDomain::IsAttached メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa9576f568ef1f6da3eef812abb9674aa0d81dfb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996165"
---
# <a name="icordebugappdomainisattached-method"></a>ICorDebugAppDomain::IsAttached メソッド
アプリケーション ドメインに、デバッガーがアタッチされているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbAttached`  
 [out]`true`デバッガーがアプリケーション ドメインに接続されている。 それ以外の場合`false`します。  
  
## <a name="remarks"></a>Remarks  
 ICorDebugController メソッドは、アプリケーション ドメインに、デバッガーがアタッチされるまで使用できません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
