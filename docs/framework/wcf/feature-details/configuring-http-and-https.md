---
title: HTTP および HTTPS の WCF の構成
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 86705a4f8daa327c442ac6c53c9b44c5b5c5c2ad
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427176"
---
# <a name="configuring-http-and-https"></a>HTTP および HTTPS の構成

WCF サービスと WCF クライアントは、HTTP および HTTPS を介して通信できます。 HTTP または HTTPS の設定は、インターネット インフォメーション サービス (IIS) またはコマンド ライン ツールを使用して構成します。 WCF サービスが IIS でホストされている場合は、IIS 内で HTTP または HTTPS の設定を構成できます (inetmgr.exe ツールを使用)。 WCF サービスが自己ホスト型の場合は、コマンド ライン ツールを使用して HTTP または HTTPS の設定を構成します。

少なくとも、URL 登録を構成し、サービスで使用される URL のファイアウォールの例外を追加します。 これらの設定を構成するには、Netsh.exe ツールを使用します。

## <a name="configuring-namespace-reservations"></a>名前空間の予約を構成します。

名前空間予約では、HTTP URL 名前空間の一部に対する権限を特定のユーザー グループに割り当てます。 予約によって、名前空間のその部分でリッスンするサービスを作成する権限をユーザーに与えます。 予約は、URL プレフィックス、つまり、予約が予約パスのすべてのサブパスを説明します。 名前空間予約では、2 つの方法でワイルドカードを使用できます。 HTTP サーバー API のドキュメントについて説明します、[ワイルドカードを含む名前空間クレーム間の解決順序](/windows/desktop/Http/routing-incoming-requests)します。

実行中のアプリケーションは、同様の要求を作成して、名前空間登録を追加できます。 名前空間の同じ部分について、登録と予約の間で競合が発生します。 予約で指定された解決順序に従って登録の優先順位があります、[ワイルドカードを含む名前空間クレーム間の解決順序](/windows/desktop/Http/routing-incoming-requests)します。 この場合、実行中のアプリケーションがクレームを受信する動作が、予約によってブロックされます。

次の例では、Netsh.exe ツールを使用します。

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

このコマンドは、ドメイン \ ユーザー アカウントの指定した URL 名前空間の URL 予約を追加します。 Netsh コマンドの使用の詳細については、入力`netsh http add urlacl /?`コマンド プロンプトで Enter キーを押します。

## <a name="configuring-a-firewall-exception"></a>ファイアウォールの例外を構成します。

HTTP 経由の通信を行う WCF サービスを自己ホストする際は、例外をファイアウォール構成に追加して、特定の URL を使用した着信接続を可能にする必要があります。

## <a name="configuring-ssl-certificates"></a>SSL 証明書の構成

SSL (Secure Sockets Layer) プロトコルは、クライアントとサーバー上で証明書を使用して暗号化キーを格納します。 サーバーは、クライアントがサーバーの ID を検証できるように接続時に SSL 証明書を提供します。 また、サーバーはクライアントに証明書を要求して、接続の両側で相互認証を実行することもできます。

証明書は、接続の IP アドレスとポート番号に基づいて集中ストアに格納されます。 特別な IP アドレス 0.0.0.0 は、ローカル コンピューターの任意の IP アドレスに一致します。 証明書ストアがパスに基づく Url を区別しないことに注意してください。 同じ IP アドレスとポートの組み合わせを持つサービスは、そのサービスの URL でのパスが異なる場合でも証明書を共有する必要があります。

手順については、次を参照してください。[方法。SSL 証明書でポートを構成](how-to-configure-a-port-with-an-ssl-certificate.md)します。

## <a name="configuring-the-ip-listen-list"></a>IP リッスン一覧の構成

HTTP Server API は、ユーザーが URL を登録すると、IP アドレスとポートだけにバインドします。 既定では、HTTP Server API は、コンピューターのすべての IP アドレスに対して、URL でポートにバインドします。 HTTP Server API を使用しないアプリケーションが以前の IP アドレスとポートの組み合わせにバインドされている場合、競合が発生します。 IP リッスン一覧には、WCF サービスの一部のマシンの IP アドレス、ポートを使用するアプリケーションと共存させることができます。 IP リッスン一覧にエントリがある場合、HTTP Server API は、その一覧に指定されている IP アドレスだけにバインドします。 IP リッスン一覧を変更するには、管理特権が必要です。

Netsh ツールを使用して、次の例に示すように、IP リッスン一覧を変更します。

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>他の構成設定

<xref:System.ServiceModel.WSDualHttpBinding> を使用すると、クライアント接続では、名前空間予約と Windows ファイアウォールに対応できる既定値が使用されます。 双方向接続のクライアント ベース アドレスをカスタマイズする場合、クライアント上で HTTP 設定を行い、新しいアドレスに一致させる必要があります。

HTTP Server API は、HttpCfg からは使用できない高度な構成設定の一部です。 この設定は、レジストリで管理され、HTTP Server API を使用するシステムで実行中のすべてのアプリケーションに適用されます。 これらの設定については、次を参照してください。 [IIS 用の Http.sys レジストリ設定](https://support.microsoft.com/en-us/help/820129/http-sys-registry-settings-for-windows)します。 ほとんどのユーザーは、これらの設定を変更する必要はありません。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.WSDualHttpBinding>
- [方法: SSL 証明書を使用してポートを構成する](how-to-configure-a-port-with-an-ssl-certificate.md)
