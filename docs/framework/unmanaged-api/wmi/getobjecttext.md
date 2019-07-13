---
title: GetObjectText 関数 (アンマネージ API リファレンス)
description: GetObjectText 関数は、MOF 構文では、オブジェクトのテキストのレンダリングを返します。
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
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746495"
---
# <a name="getobjecttext-function"></a>GetObjectText 関数
管理オブジェクト フォーマット (MOF) 構文では、オブジェクトのテキストのレンダリングを返します。

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
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`lFlags`  
[in]通常は 0。 場合`WBEM_FLAG_NO_FLAVORS`(または 0x1) 修飾子は、伝達またはフレーバーの情報も指定します。

`pstrObjectText`   
[out]ポインターを`null`エントリ。 戻り時に、新しく割り当てられた`BSTR`がオブジェクトの MOF 構文のレンダリングを格納しています。  

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)メソッド。

オブジェクトに関するすべての情報が、元のオブジェクトを再作成できる MOF コンパイラのための十分な情報のみ、返される MOF テキストは含まれません。 たとえば、伝達された修飾子または親クラスのプロパティは含まれません。

メソッドのパラメーターのテキストを再構築には、次のアルゴリズムが使用します。

1. パラメーターは、その識別子の値の順序 resequenced されます。
1. パラメーターとして指定されている`[in]`と`[out]`パラメーターを 1 つに結合されます。
 
`pstrObjectText` ポインターである必要があります、`null`ポインターが解放されないため、メソッド呼び出しの前に有効な文字列をポイントする必要がありますいない、関数が呼び出されると;。

## <a name="requirements"></a>必要条件  
**プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
