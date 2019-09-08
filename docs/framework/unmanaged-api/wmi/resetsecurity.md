---
title: ResetSecurity 関数 (アンマネージ API リファレンス)
description: ResetSecurity 関数は、現在のスレッドに偽装トークンを割り当てます。
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798256"
---
# <a name="resetsecurity-function"></a>ResetSecurity 関数
指定した偽装トークンが現在のスレッドに割り当てられます。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>パラメーター

`token`  
から現在のスレッドに関連付ける偽装トークン。 この値は `null` の場合もあります。 

## <a name="return-value"></a>戻り値

関数が成功した場合、戻り値`S_OK`は (0) になります。

関数が失敗した場合、戻り値は0以外のエラーコードです。 拡張されたエラー情報を取得するには、 [GetErrorInfo](geterrorinfo.md)関数を呼び出します。
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
