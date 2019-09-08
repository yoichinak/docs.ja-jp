---
title: GetMethodQualifierSet 関数 (アンマネージ API リファレンス)
description: GetMethodQualifierSet 関数は、メソッドの修飾子セットを取得します。
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86a7788736c3c12cfcfd405de88dfadfb14c1eca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798531"
---
# <a name="getmethodqualifierset-function"></a>GetMethodQualifierSet 関数

特定のメソッドで設定された修飾子が取得されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`wszMethod`\
からメソッド名。 `wszMethod`は有効`LPCWSTR`なを指している必要があります。

`ppQualSet`\
入出力メソッドの修飾子へのアクセスを許可するインターフェイスポインターを受け取ります。 `ppQualSet` として `null` を使用することはできません。 エラーが発生した場合、新しいオブジェクトは返されず、ポインターはを`null`指すように設定されます。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドは存在しません。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが`null`です。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject:: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset)メソッドの呼び出しをラップします。

この関数の呼び出しは、現在のオブジェクトが CIM クラス定義である場合にのみサポートされます。 CIM インスタンスを指す[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)ポインターでは、メソッド操作は使用できません。

各メソッドは独自の修飾子を持つことができるため、 [IWbemQualifierSet ポインター](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)によって呼び出し元はこれらの修飾子を追加、編集、または削除できます。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
