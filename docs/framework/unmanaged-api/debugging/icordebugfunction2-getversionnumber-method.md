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
ms.openlocfilehash: 5826297d8151cf05e1ec08acbf5c9cd381d2452b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137800"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber メソッド
この関数のエディットコンティニュバージョンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pnVersion`  
 入出力この ICorDebugFunction2 オブジェクトによって表される関数のバージョン番号である整数を指すポインターです。  
  
## <a name="remarks"></a>Remarks  
 ランタイムは、デバッグセッション中に各モジュールに対して行われた編集の数を追跡します。 関数のバージョン番号は、関数を導入した編集の数を1つ超えています。 関数の元のバージョンは、バージョン1です。 この値は、そのモジュールで[ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)が呼び出されるたびに、モジュールに対してインクリメントされます。 したがって、関数の本体が `ICorDebugModule2::ApplyChanges`への最初の呼び出しと3回目の呼び出しで置き換えられた場合、`GetVersionNumber` はその関数のバージョン1、2、または4を返すことがありますが、バージョン3は返されません。 (この関数にはバージョン3はありません)。  
  
 バージョン番号は、モジュールごとに個別に追跡されます。 したがって、モジュール1で4つの編集を実行し、モジュール2では何も実行しない場合、モジュール1の次の編集では、モジュール1のすべての編集された関数にバージョン番号6が割り当てられます。 同じ編集がモジュール2の場合、モジュール2の関数のバージョン番号は2になります。  
  
 `GetVersionNumber` メソッドによって取得されたバージョン番号は、 [GetCurrentVersionNumber 関数::](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)によって取得された値よりも小さくなる場合があります。  
  
 [コード:: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)メソッドは、`ICorDebugFunction2::GetVersionNumber`と同じ操作を実行します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
