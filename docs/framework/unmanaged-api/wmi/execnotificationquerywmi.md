---
title: ExecNotificationQueryWmi 関数 (アンマネージ API リファレンス)
description: ExecNotificationQueryWmi 関数は、イベントを受信するクエリを実行します。
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cac00ff96d0c7007bdd6135282c3f767217385e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352881"
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi 関数

イベントを受信するクエリが実行されます。 呼び出しが直ちに返され、呼び出し元は、到着すると、イベントの返された列挙子をポーリングします。 返された列挙子を解放するクエリをキャンセルします。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

`strQueryLanguage`\
[in]Windows の管理でサポートされる有効なクエリ言語を含む文字列。 WMI クエリ言語の頭字語である"WQL"必要があります。

`strQuery`\
[in]クエリのテキスト。 このパラメーターを `null` とすることはできません。

`lFlags`\
[in]この関数の動作に影響する次の 2 つのフラグの組み合わせ。 これらの値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

| 定数 | 値  | 説明  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグには、半同期的メソッドの呼び出しが行わします。 このフラグが設定されていない場合、呼び出しが失敗します。 これは、イベントが継続的に、受信したため、ユーザーは、返された列挙子をポーリングする必要があります。 この呼び出しを無期限にブロックしているようにを不可能になります。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 関数は、順方向専用の列挙子を返します。 呼び出しは許可されませんが、通常、順方向専用の列挙子は、高速と従来の列挙子より少ないメモリを使用して、[複製](clone.md)します。 |

`pCtx`\
[in]この値は、通常、`null`します。 ポインターは、それ以外の場合、 [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)要求イベントを提供しているプロバイダーで使用できるインスタンス。

`ppEnum`\
[out]エラーが発生しない場合は、クエリの結果セットのインスタンスを取得する呼び出し元を許可する列挙子へのポインターを受け取ります。 参照してください、[解説](#remarks)詳細についてはします。

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
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、1 つ以上の関数が返すことができるクラスを表示するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | クエリでは、存在しないクラスを指定します。 |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | イベントの配信が多すぎるの精度が要求されています。 大規模なポーリングの許容範囲を指定する必要があります。 |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | クエリでは、Windows の管理を提供できるより多くの情報を要求します。 これは、`HRESULT`イベント クエリの結果を名前空間のすべてのオブジェクトのポーリング要求したときに返されます。 |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | クエリでは、構文エラーがありました。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 要求されたクエリ言語がサポートされていません。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | クエリが複雑すぎます。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと WMI のリモート プロシージャ コール (RPC) リンクに失敗しました。 |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | クエリを解析できません。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery)メソッド。

呼び出し元が、返されたは定期的に、関数から制御が戻た後`ppEnum`オブジェクトを[次](next.md)関数を使用可能なイベントがあるを参照してください。

数に制限は`AND`と`OR`WQL クエリで使用できるキーワードです。 WMI を返す可能性が多数の複雑なクエリで使用される WQL キーワード、 `WBEM_E_QUOTA_VIOLATION` (または 0x8004106c) としてのエラー コード、`HRESULT`値。 WQL キーワードの制限は、クエリの複雑な方法に依存します。

呼び出すことによって追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)