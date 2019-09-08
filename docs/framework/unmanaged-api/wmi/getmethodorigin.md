---
title: GetMethodOrigin 関数 (アンマネージ API リファレンス)
description: GetMethodOrigin 関数は、メソッドが宣言されているクラスを特定します。
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cea7251353dae093f64448c8d84157917fa74c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798558"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin 関数
メソッドを宣言しているクラスが特定されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`wszMethodName`  
から所有クラスが要求されているオブジェクトのメソッドの名前。 

`pstrClassName`  
入出力メソッドを所有するクラスの名前を受け取ります。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドが見つかりませんでした。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1つ以上のパラメーターが無効です。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject:: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)メソッドの呼び出しをラップします。

クラスは1つまたは複数の基底クラスからメソッドを継承できるため、多くの場合、開発者は特定のメソッドが定義されているクラスを特定する必要があります。

パラメーター `pstrClassName`であるため`out` 、関数が呼び出さ`BSTR`れる前に、パラメーターは有効なを指していない必要があります。このポインターは、関数から制御が戻った後に割り当て解除されません。

## <a name="requirements"></a>必要条件  
**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
