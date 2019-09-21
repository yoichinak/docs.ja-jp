---
title: ConnectServerWmi 関数 (アンマネージ API リファレンス)
description: ConnectServerWmi 関数は、DCOM を使用して WMI 名前空間への接続を作成します。
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
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798754"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi 関数

指定したコンピューターにある WMI 名前空間との接続が DCOM 経由で作成されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
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
から正しい WMI 名前空間`BSTR`のオブジェクトパスを含む有効なへのポインター。 詳細については、「[解説](#remarks)」を参照してください。

`strUser`\
からユーザー名を格納し`BSTR`ている有効なへのポインター。 値`null`は、現在のセキュリティコンテキストを示します。 ユーザーが現在のドメインとは異なるドメインにある場合、 `strUser`には、円記号で区切られたドメインとユーザー名を含めることもできます。 `strUser`は、 `userName@domainName`などのユーザープリンシパル名 (UPN) 形式で指定することもできます。 詳細については、「[解説](#remarks)」を参照してください。

`strPassword`\
からパスワードを格納して`BSTR`いる有効なへのポインター。 は`null` 、現在のセキュリティコンテキストを示します。 空の文字列 ("") は、長さ0の有効なパスワードを示します。

`strLocale`\
から情報取得の正しいロケール`BSTR`を示す有効なへのポインター。 Microsoft ロケール識別子の場合、文字列の形式は "MS\_*xxx*" です。ここで、 *xxx*はロケール識別子 (LCID) を示す16進数形式の文字列です。 無効なロケールが指定されている場合`WBEM_E_INVALID_PARAMETER` 、このメソッドは Windows 7 以外のを返します。この場合、サーバーの既定のロケールが代わりに使用されます。 ' Null1 ' の場合、現在のロケールが使用されます。

`lSecurityFlags`\
から`ConnectServerWmi`メソッドに渡すフラグ。 このパラメーターの値がゼロ (0) の場合は、サーバーへ`ConnectServerWmi`の接続が確立された後にのみ、が返されます。 これにより、サーバーが破損した場合にアプリケーションが無期限に応答しなくなる可能性があります。 その他の有効な値は次のとおりです。

| 定数  | Value  | 説明  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | 内部使用のために予約されています。 使わないでください。 |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`2分以内にを返します。 |

`strAuthority`\
からユーザーのドメイン名。 次の値のいずれかを取ります。

| 値 | 説明 |
|---------|---------|
| 空白 | NTLM 認証が使用され、現在のユーザーの NTLM ドメインが使用されます。 で`strUser`ドメインが指定されている場合 (推奨される場所)、ここで指定しないでください。 両方のパラメーター `WBEM_E_INVALID_PARAMETER`でドメインを指定した場合、関数はを返します。 |
| Kerberos:*プリンシパル名* | Kerberos 認証が使用され、このパラメーターには Kerberos プリンシパル名が含まれます。 |
| NTLMDOMAIN:*ドメイン名* | NT LAN Manager 認証が使用され、このパラメーターには NTLM ドメイン名が含まれます。 |

`pCtx`\
から通常、このパラメーターは`null`です。 それ以外の場合は、1つまたは複数の動的クラスプロバイダーが必要とする[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)オブジェクトへのポインターです。

`ppNamespace`\
入出力関数から制御が戻るときに、指定した名前空間にバインドされている[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)オブジェクトへのポインターを受け取ります。 エラーが発生したとき`null`にを指すように設定されています。

`impLevel`\
から偽装レベル。

`authLevel`\
から承認レベル。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが有効ではありません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するために必要なメモリが不足しています。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver)メソッドの呼び出しをラップします。

既定の名前空間へのローカルアクセス`strNetworkResource`の場合、には単純なオブジェクトパス ("root\default\\" または ".\root\default") を指定できます。 COM または Microsoft と互換性のあるネットワークを使用してリモートコンピューター上の既定の名前空間にアクセスする\\には、コンピューター名 "myserver\root\default" を含めます。 コンピューター名には、DNS 名または IP アドレスを指定することもできます。 また`ConnectServerWmi` 、ipv6 アドレスを使用して、ipv6 を実行しているコンピューターに接続することもできます。

`strUser`を空の文字列にすることはできません。 ドメインがで`strAuthority`指定されている場合は、に`strUser`も含めることができません`WBEM_E_INVALID_PARAMETER`。また、関数はを返します。

## <a name="requirements"></a>必要条件

 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** WMINet_Utils

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
