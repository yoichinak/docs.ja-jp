---
title: PutMethod 関数 (アンマネージ API リファレンス)
description: PutMethod 関数は、メソッドを作成します。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99bc65b0181a7c0ab7877273b3747ece91544f99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049259"
---
# <a name="putmethod-function"></a>PutMethod 関数
メソッドが作成されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`wszName`  
[in]作成するメソッドの名前。 

`lFlags`  
[in] 予約されています。 このパラメーターは、0 を指定する必要があります。

`pSignatureIn`  
[in]コピーへのポインター、 [_parameters システム クラス](/windows/desktop/WmiSdk/--parameters)を格納している、`in`メソッドのパラメーター。 場合、このパラメーターは無視されます設定`null`します。  

`pSignatureOut`  
[in] コピーへのポインター、 [_parameters システム クラス](/windows/desktop/WmiSdk/--parameters)を格納している、`out`メソッドのパラメーター。 場合、このパラメーターは無視されます設定`null`します。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが無効です。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]`メソッド パラメーターの両方で指定された、 *pInSignature*と*pOutSignature*オブジェクトが別の修飾子を持ちます。
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | メソッドのパラメーターでの指定が不足している、 **ID**修飾子。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | メソッドのパラメーターに割り当てられている ID のシリーズでは、連続がないか、0 から始まっていません。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | メソッドの戻り値が、 **ID**修飾子。 |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | 親クラスから既存のメソッド名を再利用しようし、署名が一致しませんでした。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。 |
  
## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)メソッド。

場合にのみ、このメソッドの呼び出しがサポート`ptr`CIM クラスの定義を示します。 メソッドの操作をからご利用いただけません[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) CIM インスタンスを指すポインター。

ユーザーは、アンダー スコアで開始または終了する名前を持つメソッドを作成することはできません。 これはシステム クラスとプロパティの予約されています。

メソッドで、`in`と`out`パラメーターはプロパティとして説明[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)オブジェクト。

`[in/out]`によって示される両方のオブジェクトへの同じプロパティを追加することでパラメーターを定義することができます、`pInSignature`と`pOutSignature`パラメーター。 この場合、プロパティが同じ共有**ID**修飾子の値。

内の各プロパティを[_parameters](/windows/desktop/WmiSdk/--parameters)以外のオブジェクトをクラス`ReturnValue`必要があります、 **ID**修飾子、パラメーターの順序を表す 0 から始まる数値です。 ない 2 つのパラメーターがある同じ**ID**値、および no **ID**値をスキップすることができます。 いずれかの条件が発生した場合、`PutMethod`関数が返される`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`します。

## <a name="example"></a>例

例については、次を参照してください。、 [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)メソッド。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
