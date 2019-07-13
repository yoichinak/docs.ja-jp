---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f38f9a3ebd88e0a5abb7a6bc8cb4026dc7d0f068
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736939"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド
ガベージ コレクション ハンドルが、指定した管理対象のオブジェクト参照ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `handle`  
 [in]ガベージ コレクション ハンドルを持つマネージ オブジェクトへのポインター。 この値は、<xref:System.IntPtr>オブジェクトおよびから取得できます、<xref:System.Runtime.InteropServices.GCHandle>マネージ オブジェクト。  
  
 `pOutValue`  
 [out]指定したマネージ オブジェクトへの参照を表す ICorDebugReferenceValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 ガベージ コレクションの参照を値で返される参照値を混同しないでください。  
  
 返される参照は、通常の参照のように動作します。 ブレークポイントの後でコードが実行が継続する場合に無効です。 ターゲット オブジェクトの有効期間は参照値の有効期間の影響を受けません。  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle`メソッドは、ハンドルは検証されません。 そのため、`GetReferenceValueFromGCHandle`デバッガーと無効なハンドルが渡された場合にデバッグ中のコードの両方、メソッドは破損可能性があることができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
