---
title: ConnectServerWmi 関数 (アンマネージ API リファレンス)
description: ConnectServerWmi 関数では、DCOM を使用して、WMI 名前空間への接続を作成します。
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 548c6007d4ed685c521676de87c5a98f56a222a4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376989"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi 関数
指定したコンピューターにある WMI 名前空間との接続が DCOM 経由で作成されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```
## <a name="parameters"></a>パラメーター

`strNetworkResource`\
[in]有効なポインター`BSTR`正しい WMI 名前空間のオブジェクトのパスを格納しています。 参照してください、[解説](#remarks)詳細についてはします。

`strUser`\
[in]有効なへのポインター`BSTR`ユーザー名を格納しています。 A`null`値が現在のセキュリティ コンテキストを示します。 場合、ユーザーは、現在の 1 つの異なるドメインから`strUser`円記号で区切られたドメインとユーザー名を含めることもできます。 `strUser` できるようにユーザー プリンシパル名 (UPN) 形式でも`userName@domainName`します。 参照してください、[解説](#remarks)詳細についてはします。

`strPassword`\
[in]有効なへのポインター`BSTR`パスワードを格納しています。 A`null`現在のセキュリティ コンテキストを示します。 空の文字列 ("")、有効な長さ 0 のパスワードを示します。

`strLocale`\
[in]有効なへのポインター`BSTR`情報の取得を適切なロケールを示します。 マイクロソフト ロケールの識別子、文字列の形式は"MS\_*xxx*"ここで、 *xxx*文字列がロケール識別子 (LCID) を示す 16 進数形式です。 無効なロケールが指定されているかどうか、メソッドを返します`WBEM_E_INVALID_PARAMETER`Windows 7、サーバーの既定のロケールが代わりに使用される場合は除きます。 場合 ' null 1、現在のロケールを使用します。 
 
`lSecurityFlags`\
[in]渡すフラグ、`ConnectServerWmi`メソッド。 このパラメーターにゼロ (0) の値の結果への呼び出しで`ConnectServerWmi`サーバーへの接続が確立された後にのみを返します。 これは、結果、応答していない無期限に、サーバーが切断されたかどうか、アプリケーション。 その他の有効な値は次のとおりです。

| 定数  | 値  | 説明  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | 内部使用のために予約されています。 使用しないでください。 |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` 2 分以内に返されます。 |

`strAuthority`\
[in]ユーザーのドメイン名。 次の値のいずれかを取ります。

| [値] | 説明 |
|---------|---------|
| 空白 | NTLM 認証を使用して、現在のユーザーの NTLM ドメインが使用されます。 場合`strUser`ドメイン (推奨される場所) を指定します。 ここで指定しない必要がありますに。 関数を返します`WBEM_E_INVALID_PARAMETER`両方のパラメーターでドメインを指定する場合。 |
| Kerberos:*プリンシパル名* | Kerberos 認証を使用して、このパラメーターには、Kerberos プリンシパル名が含まれています。 |
| NTLMDOMAIN:*ドメイン名* | NT LAN Manager 認証を使用して、このパラメーターには、NTLM ドメイン名が含まれています。 |

`pCtx`\
[in]このパラメーターは、通常、`null`します。 ポインターは、それ以外の場合、 [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)オブジェクトが 1 つまたは複数の動的クラス プロバイダーが必要です。 

`ppNamespace`\
[out]ポインターを受け取る関数が戻るとき、 [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)オブジェクトを指定した名前空間にバインドします。 をポイントに設定されている`null`エラーがあるとします。

`impLevel`\
[in]偽装レベル。

`authLevel`\
[in]承認レベル。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver)メソッド。

既定の名前空間へのローカル アクセスの`strNetworkResource`簡単なオブジェクト パスを指定することができます。"root \default"または"\\.\root\default"。 リモート コンピューター上の既定の名前空間にアクセスするため、COM や Microsoft と互換性のあるネットワークを使用して、コンピューター名を含める:"\\myserver\root\default"。 コンピューター名は、DNS 名または IP アドレスを使用することも。 `ConnectServerWmi`関数は IPv6 を実行しているコンピューターにも接続できる IPv6 アドレスを使用します。

`strUser` 空の文字列にすることはできません。 ドメインがで指定されている場合`strAuthority`、いないも含める必要がありますで`strUser`、関数を返しますまたは`WBEM_E_INVALID_PARAMETER`します。


## <a name="requirements"></a>必要条件

 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** WMINet_Utils.idl

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)