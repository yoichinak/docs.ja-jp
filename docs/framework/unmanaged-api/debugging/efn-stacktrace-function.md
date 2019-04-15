---
title: _EFN_StackTrace 関数
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfbdbb389f9945ffeea649bcddd45bee8caf2496
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119991"
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace 関数
マネージド スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージド コードとマネージド コードの間の各移行につき 1 つ) を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `Client`  
 [in]デバッグ中のクライアント。  
  
 `wszTextOut`  
 [out]スタック トレースのテキスト表現。  
  
 `puiTextLength`  
 [out]文字数へのポインター`wszTextOut`します。  
  
 `pTransitionContexts`  
 [out]コンテキストの切り替えの配列。  
  
 `puiTransitionContextCount`  
 [out]配列内の遷移のコンテキストの数へのポインター。  
  
 `uiSizeOfContext`  
 [in]Context 構造体のサイズ。  
  
 `Flags`  
 [in]0 または SOS_STACKTRACE_SHOWADDRESSES (0x01) のいずれかに設定すると、EBP レジスタとそれぞれの前に入力スタック ポインター (ESP) を表示する`module!functionname`行。  
  
## <a name="remarks"></a>Remarks  
 `_EFN_StackTrace`構造体は、WinDbg プログラマティック インターフェイスから呼び出すことができます。 パラメーターは、次のように使用されます。  
  
-   場合`wszTextOut`が null と`puiTextLength`が null でない関数は、返す文字列の長さで`puiTextLength`します。  
  
-   場合`wszTextOut`が null でないテキストでは、関数には格納`wszTextOut`によって示される位置まで`puiTextLength`します。 バッファーの長さが不足している場合、バッファー、または返します E_OUTOFMEMORY で十分な空き領域が認識されたかどうかを正常に返します。  
  
-   場合、関数の遷移の部分は無視されます`pTransitionContexts`と`puiTransitionContextCount`はどちらも null です。 この場合、関数は、関数名のみのテキスト出力を持つ呼び出し元を提供します。  
  
-   場合`pTransitionContexts`が null と`puiTransitionContextCount`が null でない関数返しますコンテキスト エントリのために必要な数`puiTransitionContextCount`します。  
  
-   場合`pTransitionContexts`が null でない関数として扱われます長さの構造体の配列`puiTransitionContextCount`します。 構造体のサイズがで指定された`uiSizeOfContext`のサイズを指定する必要があります[SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)または`CONTEXT`のアーキテクチャ。  
  
-   `wszTextOut` 次の形式で書き込まれます。  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   16 進数でオフセットが「0x0」の場合、オフセットは書き込まれません。  
  
-   コードがないマネージ スレッドの現在のコンテキストで、関数は SOS_E_NOMANAGEDCODE を返します。  
  
-   `Flags`パラメーターが 0 またはそれぞれの前に、EBP と ESP を表示する SOS_STACKTRACE_SHOWADDRESSES`module!functionname`行。 既定では、これは 0 です。  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** SOS_Stacktrace.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
