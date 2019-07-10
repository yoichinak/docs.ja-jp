---
title: QualifierSet_Next 関数 (アンマネージ API リファレンス)
description: QualifierSet_Next 関数は、列挙体で、[次へ] 修飾子を取得します。
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ac5cc8633881749bdc167e1b3925a83f7adf3b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760303"
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next 関数
[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 関数の呼び出しによって開始された列挙型内の次の修飾子が返されます。   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`   
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)インスタンス。

`lFlags`   
[in] 予約されています。 このパラメーターは、0 を指定する必要があります。

`pstrName`   
[out]修飾子の名前。 場合`null`、このパラメーターは無視されます。 それ以外`pstrName`、有効なをポイントする必要がありますいない`BSTR`またはメモリ リークが発生します。 かどうかは null でない関数は、常に割り当て、新しい`BSTR`を返す場合`WBEM_S_NO_ERROR`します。

`pVal`   
[out]成功した場合、修飾子の値。 関数が失敗した場合、`VARIANT`によって示される`pVal`は変更されません。 このパラメーターが場合`null`パラメーターは無視されます。

`plFlavor`   
[out]修飾子のフレーバーを受信する長整数型へのポインター。 このパラメーターを指定できますフレーバー情報が望ましくない場合`null`します。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼び出し元が呼び出さなかった[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)します。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するのに十分なメモリがあります。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙型でその他の修飾子が残されません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)メソッド。

呼び出す、`QualifierSet_Next`関数の戻り値までのすべての修飾子を列挙するために繰り返し関数`WBEM_S_NO_MORE_DATA`します。 列挙体を早い段階を終了するには、呼び出し、 [QualifierSet_EndEnumeration](qualifierset-endenumeration.md)関数。

列挙時に返される修飾子の順序は定義されません。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
