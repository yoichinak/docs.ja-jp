---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1cab24f949ddae55d5e699e6ad82851007504dd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475698"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド
ランタイムにそのイメージを現在のプロセスに読み込むためにプリコンパイル済みのイメージに埋め込む必要があるフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pdwFlags`  
 [in]値、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)コンパイラ フラグを指定する列挙体に適切なコンパイル済みのイメージを選択するために使用します。  
  
## <a name="remarks"></a>Remarks  
 `SetDesiredNGENCompilerFlags`メソッドは、ランタイムはこのプロセスにそのイメージを読み込むようにプリコンパイル済みのイメージに埋め込む必要があるフラグを指定します。 このメソッドによって設定されたフラグは、適切なプリコンパイル済みのイメージの選択にのみ使用されます。 このようなイメージが存在しない場合、ランタイムは読み込む Microsoft intermediate language (MSIL) のイメージと、ジャストイン タイム (JIT) コンパイラ代わりにします。 その場合は、デバッガーを使用する必要がありますが、 [icordebugmodule 2::setjitcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)メソッドを JIT コンパイルの必要に応じて、フラグを設定します。  
  
 イメージが読み込まれると、JIT コンパイルはいくつか行う必要があります (これは、イメージには、ジェネリックが含まれている場合、ケースになります) そのイメージの場合で指定されたコンパイラ フラグ、`SetDesiredNGENCompilerFlags`メソッドは、追加の JIT コンパイルに適用されます。  
  
 `SetDesiredNGENCompilerFlags`メソッドを呼び出す必要があります、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバック。 呼び出そうとすると、`SetDesiredNGENCompilerFlags`メソッドが後では失敗します。 もないか、フラグを設定しようとが定義されている、`CorDebugJITCompilerFlags`列挙型または指定されたプロセスの有効ではないが失敗します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
