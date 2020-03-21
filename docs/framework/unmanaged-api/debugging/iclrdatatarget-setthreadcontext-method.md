---
title: ICLRDataTarget::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179125"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext メソッド
ターゲット プロセス内の指定したスレッドの現在のコンテキストを設定します。 このメソッドは、共通言語ランタイム (CLR) のデータ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]ターゲット プロセス内のスレッドのオペレーティング システム識別子。  
  
 `contextSize`  
 [in]コンテキストのサイズ。  
  
 `context`  
 [in]コンテキストを含むバッファーへのポインター。  
  
 バッファー内の`context`データは、Win32`CONTEXT`構造体の形式になります。 コンテキストはプロセッサ固有のレジスタ データを指定するため、Win32`CONTEXT`構造体の定義はプロセッサのアーキテクチャによって異なります。 Win32`CONTEXT`構造体の定義については、WinNT.h ヘッダー ファイルを参照してください。  
  
## <a name="remarks"></a>解説  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** をします。  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)
