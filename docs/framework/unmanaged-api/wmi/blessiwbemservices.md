---
title: BlessIWbemServices 関数 (アンマネージ API リファレンス)
description: BlessIWbemServices 関数では、ユーザーの資格情報が、IWbemServices クラスへのアクセスを許可するかどうかを示します。
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23b72856015d028e50c1e3bfd4a12e0f220291c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354610"
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices 関数
ユーザーの資格情報が指定したへのアクセスを許可するかどうかを示す[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)クラス。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>パラメーター

`pIWbemServices`\
[in]ポインター、 [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)オブジェクトの権限が必要です。

`strUser`\
[in]ユーザー名。

`strPassword`\
[in]関連付けられているパスワード`strUser`します。

`strAuthority`\
[in]ユーザーのドメイン名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`impLevel`\
[in]偽装レベル。

`authnLevel`\
[in]承認レベル。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WinError.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 1 つまたは複数の引数が無効です。 |
| `E_POINTER` | 0x80004003 | `pIWbemServices` は `null` です。 | 
| `E_FAIL` | 0x80000008 | 不明なエラーが発生しました。 |
| `E_OUTOFMEMORY` | 0x80000002 | メモリ不足のためでは、操作を実行します。 | 
| `S_OK` | 0 | 関数呼び出しに成功しました。 | 

## <a name="requirements"></a>必要条件  

 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)