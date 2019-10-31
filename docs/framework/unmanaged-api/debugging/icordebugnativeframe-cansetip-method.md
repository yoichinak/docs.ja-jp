---
title: ICorDebugNativeFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: b3758ac1a84092b8bf2678f9cc2c19c9d9961690
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137322"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP メソッド
命令ポインター (IP) をネイティブコード内の指定されたオフセット位置に安全に設定できるかどうかを示す HRESULT を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `nOffset`  
 から命令ポインターに必要な設定。  
  
## <a name="remarks"></a>Remarks  
 `CanSetIP` メソッドを使用して、このメソッドを[実行](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)します。 `CanSetIP` が S_OK 以外の HRESULT を返す場合でも、`ICorDebugNativeFrame::SetIP`を呼び出すことはできますが、デバッガーがデバッグ中のコードの安全かつ適切な実行を継続する保証はありません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
