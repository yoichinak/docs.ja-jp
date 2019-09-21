---
title: GetObjectText 関数 (アンマネージ API リファレンス)
description: GetObjectText 関数は、MOF 構文でオブジェクトのテキスト形式のレンダリングを返します。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d47fcd59204a4d114fc9f0dc5bc4550ba1681f33
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798508"
---
# <a name="getobjecttext-function"></a>GetObjectText 関数
管理オブジェクトフォーマット (MOF) 構文におけるオブジェクトのテキスト形式のレンダリングを返します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`lFlags`  
から通常は0です。 ( `WBEM_FLAG_NO_FLAVORS`または 0x1) が指定されている場合、修飾子は伝達またはフレーバー情報なしに含まれます。

`pstrObjectText`   
入出力`null` On エントリへのポインター。 返されると、オブジェクトの`BSTR` MOF 構文レンダリングを含む新しく割り当てられた。  

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが有効ではありません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するために必要なメモリが不足しています。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)メソッドの呼び出しをラップします。

返される MOF テキストには、オブジェクトに関する情報がすべて含まれているわけではありませんが、MOF コンパイラが元のオブジェクトを再作成するのに十分な情報のみが含まれています。 たとえば、伝達された修飾子や親クラスのプロパティは含まれません。

次のアルゴリズムは、メソッドのパラメーターのテキストを再構築するために使用されます。

1. パラメーターは、識別子の値の順序で再シーケンスされます。
1. `[in]` および`[out]`として指定されたパラメーターは、1つのパラメーターに結合されます。
 
`pstrObjectText`は、関数が呼び出され`null`たときにへのポインターである必要があります。ポインターが割り当て解除されないため、メソッド呼び出しの前に有効な文字列を指すことはできません。

## <a name="requirements"></a>必要条件  
**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
