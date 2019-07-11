---
title: SetSecurity 関数 (アンマネージ API リファレンス)
description: SetSecurity 関数は、現在のスレッドの偽装トークンを取得します。
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2cb71263201c86a93ca0bfbd783f2b8512055e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783118"
---
# <a name="setsecurity-function"></a>SetSecurity 関数

現在のスレッドに関連付けられている偽装トークンが取得されます。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a>パラメーター

`pNeedToReset`\
[out]関数から制御が戻るときにへのポインターを格納する`boolean`を呼び出してトークンをリセットするかどうかを示す、 [ResetSecurity](resetsecurity.md)関数。

`token`\
[out]関数から制御が戻るときは、現在のスレッドに関連付けられている権限借用トークンのハンドルへのポインターを格納します。 その値を指定できます`null`かどうかは、現在のスレッドに関連付けられているトークンはありません。 

## <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は`S_OK`(0)。

関数が失敗した場合、戻り値が 0 以外のエラー コードにします。 拡張エラー情報を取得する、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件

 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** WMINet_Utils.idl

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
