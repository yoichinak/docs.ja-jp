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
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798238"
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
入出力関数から制御が戻るときに、 `boolean` [resetsecurity](resetsecurity.md)関数を呼び出すことによってトークンをリセットする必要があるかどうかを示すへのポインターを格納します。

`token`\
入出力関数から制御が戻るときに、現在のスレッドに関連付けられている偽装トークンのハンドルへのポインターを格納します。 現在のスレッドに`null`関連付けられているトークンが存在しない場合は、その値をにすることができます。 

## <a name="return-value"></a>戻り値

関数が成功した場合、戻り値`S_OK`は (0) になります。

関数が失敗した場合、戻り値は0以外のエラーコードです。 拡張されたエラー情報を取得するには、 [GetErrorInfo](geterrorinfo.md)関数を呼び出します。

## <a name="requirements"></a>必要条件

 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** WMINet_Utils

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
