---
title: ExecQueryWmi 関数 (アンマネージ API リファレンス)
description: ExecQueryWmi 関数では、オブジェクトを取得するクエリを実行します。
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 402bbcb9ad5e462a55c5ec2716417f512f03ee19
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373219"
---
# <a name="execquerywmi-function"></a>ExecQueryWmi 関数

オブジェクトを取得するクエリが実行されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT ExecQueryWmi (
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
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

| 定数 | 値  | 説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | セット、関数は、現在の接続のロケールのローカライズされた名前空間に格納されている修正済みの修飾子を取得します。 場合、 <br/> 指定しない場合、セット、関数は、即時の名前空間に格納されている修飾子のみを取得します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグには、半同期的メソッドの呼び出しが行わします。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 関数は、順方向専用の列挙子を返します。 呼び出しは許可されませんが、通常、順方向専用の列挙子は、高速と従来の列挙子より少ないメモリを使用して、[複製](clone.md)します。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI は、リリースされるまでに、列挙内のオブジェクトへのポインターを保持します。 |
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | 返されるオブジェクトがあるのに十分な情報にそのためことにより、そのシステムのプロパティなど **_path**、 **_ _relpath**と **_ _server**、いない`null`。 |
| `WBEM_FLAG_PROTOTYPE` | 2 | このフラグは、プロトタイプの作成に使用されます。 クエリを実行しないと、代わりに、通常の結果オブジェクトのようなオブジェクトを返します。 |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | エラーの原因は直接の親クラスまたはサブクラスに関係なく指定されたクラスのプロバイダーへのアクセスです。 |

推奨されるフラグは`WBEM_FLAG_RETURN_IMMEDIATELY`と`WBEM_FLAG_FORWARD_ONLY`最適なパフォーマンス。

`pCtx`\
[in]この値は、通常、`null`します。 ポインターは、それ以外の場合、 [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)インスタンスを要求されたクラスを提供しているプロバイダーによって使用されることができます。

`ppEnum`\
[out]エラーが発生しない場合は、クエリの結果セットのインスタンスを取得する呼び出し元を許可する列挙子へのポインターを受け取ります。 クエリでは、0 個のインスタンスを含む結果セットを持つことができます。 参照してください、[解説](#remarks)詳細についてはします。

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
| `WBEM_E_INVALID_QUERY` | 0x80041017 | クエリでは、構文エラーがありました。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 要求されたクエリ言語がサポートされていません。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | クエリが複雑すぎます。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと WMI のリモート プロシージャ コール (RPC) リンクに失敗しました。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | クエリでは、存在しないクラスを指定します。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery)メソッド。

この関数で指定されたクエリの処理、`strQuery`パラメーターと、呼び出し元が、クエリ結果のアクセス時に使用する列挙子を作成します。 列挙子がへのポインター、 [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)インターフェイスは、クエリ結果はをとおして利用可能なクラスのオブジェクトのインスタンス、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インターフェイス。

数に制限は`AND`と`OR`WQL クエリで使用できるキーワードです。 WMI を返す可能性が多数の複雑なクエリで使用される WQL キーワード、 `WBEM_E_QUOTA_VIOLATION` (または 0x8004106c) としてのエラー コード、`HRESULT`値。 WQL キーワードの制限は、クエリの複雑な方法に依存します。

呼び出すことによって追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)