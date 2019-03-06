---
title: GetPropertyQualifierSet 関数 (アンマネージ API リファレンス)
description: GetPropertyQualifierSet 関数は、プロパティの設定、修飾子を取得します。
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdb9f748279e4e74c0dbd1ced1f48e3a24b9904d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358419"
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet 関数

特定のプロパティで設定された修飾子が取得されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`wszMethod`\
[in]プロパティ名。 `wszProperty` 有効なをポイントする必要があります`LPCWSTR`します。

`ppQualSet`\
[out]プロパティの修飾子にアクセスできるインターフェイス ポインターを受け取ります。 `ppQualSet` として `null` を使用することはできません。 かどうかは、エラーが発生し、新しいオブジェクトは返されませんを指すポインターを設定`null`します。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドが存在しません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが`null`します。 |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | 関数は、システム プロパティの修飾子を取得しようとします。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset)メソッド。

この関数の呼び出しがサポートされるは、現在のオブジェクトが CIM クラスの定義である場合にのみです。 メソッドの操作は利用できません[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) CIM インスタンスを指すポインター。

各メソッドには、独自の修飾子が可能性があるため、 [IWbemQualifierSet ポインター](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)により、呼び出し元を追加、編集、またはこれらの修飾子を削除します。

システムのプロパティは修飾子を持たないため、関数を返します`WBEM_E_SYSTEM_PROPERTY`を取得しようとした場合、 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)システム プロパティへのポインター。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)