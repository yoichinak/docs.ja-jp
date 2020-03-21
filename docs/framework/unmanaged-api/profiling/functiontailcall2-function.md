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
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175188"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 関数
現在実行中の関数が別の関数に対して末尾呼び出しを実行しようとしていることをプロファイラーに通知し、スタック フレームに関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>パラメーター

- `funcId`

  \[in] 末尾呼び出しを行おうとしている現在実行中の関数の識別子。

- `clientData`

  \[in] 再マップされた関数識別子( プロファイラーが以前に[FunctionIDMapper](functionidmapper-function.md)を介して指定した) で、現在実行されている末尾呼び出しを行おうとしている関数の識別子です。
  
- `func`

  \[in]`COR_PRF_FRAME_INFO`スタック フレームに関する情報を指す値。

  プロファイラーは、[これを ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)メソッドの実行エンジンに返すことができる不透明なハンドルとして扱う必要があります。

## <a name="remarks"></a>解説  
 テールコールのターゲット関数は現在のスタックフレームを使用し、テールコールを行った関数の呼び出し元に直接戻ります。 これは、Tail 呼び出しの対象である関数に対して[FunctionLeave2](functionleave2-function.md)コールバックが発行されないことを意味します。  
  
 値が`func`変更されたり破棄されたりする可能性があるため、`FunctionTailcall2`関数が戻った後は、パラメーターの値が無効になります。  
  
 関数`FunctionTailcall2`はコールバックです。それを実装する必要があります。 実装では、 ( `__declspec``naked`) ストレージ クラス属性を使用する必要があります。  
  
 実行エンジンは、この関数を呼び出す前にレジスタを保存しません。  
  
- 入力時には、使用するすべてのレジスタ (浮動小数点単位 (FPU) 内のレジスタも含む) を保存する必要があります。  
  
- 終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップオフしてスタックを復元する必要があります。  
  
 の実装`FunctionTailcall2`はガベージ コレクションを遅延するため、ブロックしないでください。 スタックがガベージ コレクションに優しい状態ではない可能性があるため、実装はガベージ コレクションを試行しないでください。 ガベージ コレクションが試行されると、ランタイムは、戻るまで`FunctionTailcall2`ブロックします。  
  
 また、この`FunctionTailcall2`関数はマネージ コードを呼び出したり、マネージ メモリ割り当てを引き起こしたりしないでください。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コルプロフ.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [FunctionEnter2 関数](functionenter2-function.md)
- [FunctionLeave2 関数](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 メソッド](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [グローバル静的関数のプロファイル](profiling-global-static-functions.md)
