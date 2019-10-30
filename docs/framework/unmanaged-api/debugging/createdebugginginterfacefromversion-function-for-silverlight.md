---
title: CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 438af9f191f48a86207c3b343ba428eef2c1fabc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132203"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)
[Createversionstringfrommodule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)から返される共通言語ランタイム (CLR) のバージョン文字列を受け取り、対応するデバッガーインターフェイス (通常は[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szDebuggeeVersion`  
 から[Createversionstringfrommodule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)によって返される、ターゲットデバッグ対象の CLR のバージョン文字列。  
  
 `ppCordb`  
 [out] COM オブジェクト (`IUnknown`) へのポインターのポインター。 このオブジェクトは、返される前に[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトにキャストされます。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 `ppCordb` は、 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)インターフェイスを実装する有効なオブジェクトを参照します。  
  
 E_INVALIDARG  
 `szDebuggeeVersion` または `ppCordb` が null です。  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 CLR デバッグに必要なコンポーネントが見つかりません。 つまり、mscordbi.dll または mscordaccore.dll が対象の CoreCLR.dll と同じディレクトリに見つかりませんでした。  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 mscordbi.dll または mscordaccore.dll が対象の CoreCLR.dll と同じバージョンではありません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)を返すことができません。  
  
## <a name="remarks"></a>Remarks  
 返されるインターフェイスは、対象のプロセス内の CLR にアタッチして CLR が実行しているマネージド コードをデバッグする機能を提供します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** dbgshim. h  
  
 **ライブラリ:** dbgshim .dll  
  
 **.NET Framework のバージョン:** 3.5 SP1
