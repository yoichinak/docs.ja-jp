---
title: QualifierSet_Next 関数 (アンマネージ API リファレンス)
description: QualifierSet_Next 関数は、列挙体の次の修飾子を取得します。
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
ms.openlocfilehash: f97a19f236b87a7f4c5b2014aca6ee4abd338c63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798285"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next 関数
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
からこのパラメーターは使用されていません。

`ptr`   
から[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)インスタンスへのポインター。

`lFlags`   
[in] 予約されています。 このパラメーターには0を指定する必要があります。

`pstrName`   
入出力修飾子の名前。 の`null`場合、このパラメーターは無視され`pstrName`ます。それ以外の場合`BSTR` 、は有効なを指していないか、メモリリークが発生します。 Null でない場合、関数は、を返し`BSTR` `WBEM_S_NO_ERROR`たときに、常に新しいを割り当てます。

`pVal`   
入出力成功した場合は、修飾子の値。 関数が失敗`VARIANT`した場合、が指す`pVal`を変更することはできません。 このパラメーターが`null`の場合、パラメーターは無視されます。

`plFlavor`   
入出力修飾子のフレーバーを受け取る LONG へのポインター。 フレーバー情報が必要でない場合、このパラメーターは`null`にすることができます。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが有効ではありません。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼び出し元が[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)を呼び出しませんでした。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するために必要なメモリが不足しています。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙体にはそれ以上修飾子が残されていません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数は、 [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)メソッドの呼び出しをラップします。

関数が返さ`QualifierSet_Next` `WBEM_S_NO_MORE_DATA`れるまで、すべての修飾子を列挙するには、関数を繰り返し呼び出します。 列挙型を早期に終了するには、 [QualifierSet_EndEnumeration](qualifierset-endenumeration.md)関数を呼び出します。

列挙型の間に返される修飾子の順序は定義されていません。

## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
