---
title: FunctionEnter2 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177060"
---
# <a name="functionenter2-function"></a>FunctionEnter2 関数
コントロールが関数に渡されることをプロファイラーに通知し、スタック フレームと関数の引数に関する情報を提供します。 この関数は[関数の関数を置](functionenter-function.md)き換えます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>パラメーター

- `funcId`

  \[in] コントロールの受け渡し先の関数の識別子。

- `clientData`

  \[in] 再マップされた関数識別子。 [FunctionIDMapper](functionidmapper-function.md)
  
- `func`

  \[in]`COR_PRF_FRAME_INFO`スタック フレームに関する情報を指す値。
  
  プロファイラーは、[これを ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)メソッドの実行エンジンに返すことができる不透明なハンドルとして扱う必要があります。  
  
- `argumentInfo`

  \[in] 関数の引数のメモリ内の位置を指定する[COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)構造体へのポインター。

  引数情報にアクセスするには、フラグを`COR_PRF_ENABLE_FUNCTION_ARGS`設定する必要があります。 プロファイラーは、イベント フラグを設定するのに[は、](icorprofilerinfo-seteventmask-method.md)メソッドを使用できます。

## <a name="remarks"></a>解説  
 値が変更されたり`func`破棄`argumentInfo`されたりする可能性があるため、`FunctionEnter2`関数が戻った後は、 および パラメーターの値は無効になります。  
  
 関数`FunctionEnter2`はコールバックです。それを実装する必要があります。 実装では、 ( `__declspec``naked`) ストレージ クラス属性を使用する必要があります。  
  
 実行エンジンは、この関数を呼び出す前にレジスタを保存しません。  
  
- 入力時には、使用するすべてのレジスタ (浮動小数点単位 (FPU) 内のレジスタも含む) を保存する必要があります。  
  
- 終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップオフしてスタックを復元する必要があります。  
  
 の実装`FunctionEnter2`はガベージ コレクションを遅延するため、ブロックしないでください。 スタックがガベージ コレクションに優しい状態ではない可能性があるため、実装はガベージ コレクションを試行しないでください。 ガベージ コレクションが試行されると、ランタイムは、戻るまで`FunctionEnter2`ブロックします。  
  
 また、この`FunctionEnter2`関数はマネージ コードを呼び出したり、マネージ メモリ割り当てを引き起こしたりしないでください。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コルプロフ.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [FunctionLeave2 関数](functionleave2-function.md)
- [FunctionTailcall2 関数](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 メソッド](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [グローバル静的関数のプロファイル](profiling-global-static-functions.md)
