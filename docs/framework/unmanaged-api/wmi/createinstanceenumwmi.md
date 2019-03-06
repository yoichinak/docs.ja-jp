---
title: CreateInstanceEnumWmi 関数 (アンマネージ API リファレンス)
description: CreateInstanceEnumWmi 関数は、選択条件を満たす、指定されたクラスのインスタンスを含む列挙子を返します。
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a1d082cae19bd83c90e063d841a0c9e4602bc40
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373050"
---
# <a name="createinstanceenumwmi-function"></a>CreateInstanceEnumWmi 関数

指定された選択条件を満たす、指定したクラスのインスタンスを返す列挙子を返します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>パラメーター

`strFilter`\
[in]インスタンスが必要なクラスの名前。 このパラメーターを `null` とすることはできません。

`lFlags`\
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | セット、関数は、現在の接続のロケールのローカライズされた名前空間に格納されている修正済みの修飾子を取得します。 場合、 <br/> 指定しない場合、セット、関数は、即時の名前空間に格納されている修飾子のみを取得します。 |
| `WBEM_FLAG_DEEP` | 0 | 列挙体には、階層内のすべてのサブクラスとこれが含まれています。 |
| `WBEM_FLAG_SHALLOW` | 1 | 列挙体は、このクラスの純粋なインスタンスのみが含まれていますおよび、このクラスにないプロパティが指定のサブクラスのすべてのインスタンスを除外します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグには、半同期的メソッドの呼び出しが行わします。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 関数は、順方向専用の列挙子を返します。 呼び出しは許可されませんが、通常、順方向専用の列挙子は、高速と従来の列挙子より少ないメモリを使用して、[複製](clone.md)します。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI は、リリースされるまでに、列挙内のオブジェクトへのポインターを保持します。 |

推奨されるフラグは`WBEM_FLAG_RETURN_IMMEDIATELY`と`WBEM_FLAG_FORWARD_ONLY`最適なパフォーマンス。

`pCtx`\
[in]この値は、通常、`null`します。 ポインターは、それ以外の場合、 [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)インスタンスを要求されたインスタンスを提供しているプロバイダーによって使用される可能性があります。

`ppEnum`\
[out]列挙子へのポインターを受け取ります。

`authLevel`\
[in]承認レベル。

`impLevel`\
[in]偽装レベル。

`pCurrentNamespace`\
[in]ポインター、 [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)現在の名前空間を表すオブジェクト。

`strUser`\
[in]ユーザー名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`strPassword`\
[in]パスワードです。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`strAuthority`\
[in]ユーザーのドメイン名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、指定したクラスのインスタンスを表示するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strFilter` は存在しません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと WMI のリモート プロシージャ コール (RPC) リンクに失敗しました。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [iwbemservices::createclassenum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum)メソッド。

返された列挙子が要素を持たないことに注意してください。

呼び出すことによって追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)