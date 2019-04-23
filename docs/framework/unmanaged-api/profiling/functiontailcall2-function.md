---
title: FunctionTailcall2 関数
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06dd3b028f4f43ca8681c80a5caa4716104068dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080892"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 関数
現在実行中の関数が別の関数の末尾呼び出しを実行しようし、スタック フレームに関する情報を提供しますをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `funcId`  
 [in]Tail の呼び出しを行うには、現在実行中の関数の識別子です。  
  
 `clientData`  
 [in]プロファイラーを使用して以前に指定されたマップが変更された関数の識別子[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)、現在実行中の関数呼び出しの末尾に作成されるのです。  
  
 `func`  
 [in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を示す値。  
  
 プロファイラーはこれを不透明なハンドルでの実行エンジンに渡すことができるとして扱う必要があります、 [icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)メソッド。  
  
## <a name="remarks"></a>Remarks  
 末尾呼び出しの対象の関数は、現在のスタック フレームを使用し、直接 tail 呼び出しを行った関数の呼び出し元に戻ります。 つまり、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)末尾呼び出しの対象となっている関数のコールバックは発行されません。  
  
 値、`func`パラメーターが後に有効でない、`FunctionTailcall2`関数は、値が変わる可能性がありますまたは破棄されるためを返します。  
  
 `FunctionTailcall2`関数は、コールバックは、これを実装する必要があります。 実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。  
  
 実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。  
  
-   項目で、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。  
  
-   終了時に、その呼び出し元によってプッシュされたすべてのパラメーターをポップしてスタックを復元する必要があります。  
  
 実装`FunctionTailcall2`ガベージ コレクションは延期されますブロックしないでください。 実装は、ガベージ コレクションをしないで、スタックはガベージ コレクションに適した状態ではない可能性が。 ランタイムがまでブロックはガベージ コレクションが試行されると、`FunctionTailcall2`を返します。  
  
 また、`FunctionTailcall2`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
