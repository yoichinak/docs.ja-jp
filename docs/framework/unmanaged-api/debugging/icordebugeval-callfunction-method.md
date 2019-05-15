---
title: ICorDebugEval::CallFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65225281fe3abaa20e69e96f4cd4d2a4b03a87ce
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629941"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction メソッド

指定した関数の呼び出しを設定します。

このメソッドは、.NET Framework version 2.0 で廃止されています。 使用[icordebugeval 2::callparameterizedfunction](icordebugeval2-callparameterizedfunction-method.md)代わりにします。

## <a name="syntax"></a>構文

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>パラメーター

`pFunction`\
[in]呼び出される関数を指定する ICorDebugFunction オブジェクトへのポインター。

`nArgs`\
[in]関数の引数の数。

`ppArgs`\
[in]関数に渡される引数を指定する ICorDebugValue オブジェクトを指す各ポインターの配列。

## <a name="remarks"></a>Remarks

関数が仮想場合、`CallFunction`仮想ディスパッチを実行します。 関数は、別のアプリケーション ドメインでは、すべての引数がそのアプリケーション ドメイン内にも限りの移行が発生します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET framework のバージョン:** 1.1, 1.0

## <a name="see-also"></a>関連項目

- [CallParameterizedFunction メソッド](icordebugeval2-callparameterizedfunction-method.md)
