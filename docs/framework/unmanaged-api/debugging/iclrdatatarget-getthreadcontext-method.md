---
title: ICLRDataTarget::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179176"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext メソッド
ターゲット プロセス内の特定のスレッドの現在の実行コンテキストを取得します。 このメソッドは、共通言語ランタイムのデータ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]ターゲット プロセス内のスレッドのオペレーティング システム識別子。  
  
 `contextFlags`  
 [in]コンテキストのどの部分を返すかを指定するフラグ。 実装は、少なくともコンテキストのこれらの部分を返します。  
  
 `contextSize`  
 [in]コンテキストのサイズ。  
  
 `context`  
 [アウト]コンテキストを配置するバッファーへのポインター。  
  
 バッファー内の`context`データは、Win32`CONTEXT`構造体の形式である必要があります。 コンテキストはプロセッサ固有のレジスタ データを指定するため、Win32`CONTEXT`構造体の定義はプロセッサのアーキテクチャによって異なります。 Win32`CONTEXT`構造体の定義については、WinNT.h ヘッダー ファイルを参照してください。  
  
## <a name="remarks"></a>解説  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** をします。  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)
