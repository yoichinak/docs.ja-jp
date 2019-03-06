---
title: ICorDebugFunction2::GetVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497172"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber メソッド
この関数のエディット コンティニュ バージョンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pnVersion`  
 [out]ICorDebugFunction2 オブジェクトによって表される関数のバージョン番号を示す整数へのポインター。  
  
## <a name="remarks"></a>Remarks  
 ランタイムは、デバッグ セッション中に各モジュールに行われた編集回数の追跡を保持します。 関数のバージョン番号は、いずれかの関数を導入した編集の数よりも詳細です。 関数の元のバージョンは 1 です。 毎回数が、モジュールのインクリメント[icordebugmodule 2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)がそのモジュールで呼び出されます。 したがって、関数の本体は、最初と 3 番目の呼び出しで置き換えられた場合`ICorDebugModule2::ApplyChanges`、 `GetVersionNumber` 1、2、またはその関数では、4 のバージョンがバージョン 3 ではなく返す可能性があります。 (その関数がないバージョン 3 です。)  
  
 バージョン番号は、モジュールごとに個別に追跡されます。 そのため、モジュール 1、および none モジュール 2 で 4 つの編集を実行する場合に、モジュール 1 で、[次へ] の編集は 6 のバージョン番号をモジュール 1 で編集されたすべての関数に割り当てられます。 同時に編集モジュール 2、第 2 章の関数により、2 のバージョン番号が表示されます。  
  
 バージョン番号を取得して、`GetVersionNumber`メソッドによって取得するよりも低い場合があります[icordebugfunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)します。  
  
 [Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)メソッドと同じ操作を実行する`ICorDebugFunction2::GetVersionNumber`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
