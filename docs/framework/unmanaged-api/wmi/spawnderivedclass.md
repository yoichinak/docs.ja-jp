---
title: SpawnDerivedClass 関数 (アンマネージ API リファレンス)
description: SpawnDerivedClass 関数は、オブジェクトから派生した新しいオブジェクトを作成します。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f4d5219865bf7f7c9e6d284d74d0c249729dfc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040535"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass 関数
指定したオブジェクトから新たに派生するクラス オブジェクトが作成されます。    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`lFlags`  
[in] 予約されています。 このパラメーターは、0 を指定する必要があります。

`ppNewClass`  
[out]新しいクラス定義のオブジェクトへのポインターを受け取ります。 新しいオブジェクトでないエラーが発生する場合、返されると`ppNewClass`は左未変更の状態します。 その値にすることはできません`null`します。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | インスタンスからのクラスの生成などの無効な操作が要求されました。 |
| `WBEM_E_INCOMPLETE_CLASS` | ソース クラスが完全に定義されているか、Windows の管理を登録するため、新しい派生クラスは許可されていません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` は `null`です。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)メソッド。

`ptr` 生成されたオブジェクトの親クラスとなるクラス定義である必要があります。 返されるオブジェクトでは、現在のオブジェクトのサブクラスになります。

返される新しいオブジェクト`ppNewClass`自動的に現在のオブジェクトのサブクラスになります。 この動作を上書きすることはできません。 サブクラス (派生クラス) を作成できる他の方法はありません。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
