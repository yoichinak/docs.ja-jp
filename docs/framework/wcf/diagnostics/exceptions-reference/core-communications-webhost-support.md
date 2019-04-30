---
title: 'コア通信: Web ホスト サポート'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 8ee107ffcb9fab629541ce004d1c587fcad652c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998713"
---
# <a name="core-communications-webhost-support"></a>コア通信: Web ホスト サポート

ここでは、Webhost サポートによって生成されるすべての例外を示します。

## <a name="exception-list"></a>例外の一覧

|リソース コード|リソースの文字列|
|-------------------|---------------------|
|Hosting_CompatibilityServiceNotHosted|このサービスでは、ASP.NET 互換性が必要です。 また、IIS でホストする必要もあります。 Web.config で ASP.NET 互換性を有効にして IIS でサービスをホストするか、または AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode プロパティを Required 以外の値に設定します。|
|Hosting_ListenerNotFoundForActivationInRecycling|指定されたアドレスをアクティブにリッスンしているチャネルはありません。 アプリケーションがリサイクルされる場合、サービスは閉じられます。|
|Hosting_NonHTTPInCompatibilityMode|ASP.NET 互換性でサポートされるプロトコルは HTTP と HTTPS のみです。 指定されたエンドポイントを削除するか、アプリケーションに対して ASP.NET 互換性を無効にします。|
|Hosting_ProcessNotExecutingUnderHostedContext|現在のホスト環境では、指定されたホスティング プロセスを呼び出すことができません。 この API では、アプリケーションの呼び出しがインターネット インフォメーション サービスまたは Windows プロセス アクティブ化サービス内で干すとされている必要があります。|
|Hosting_ServiceCompatibilityRequire|このサービスは ASP.NET 互換性を必要とするため、アクティブにできません。 このアプリケーションに対して、ASP.NET 互換性が有効になっていません。 Web.config ファイルで ASP.NET 互換性を有効にするか、AspNetCompatibilityRequirementsAttribute.AspNetCompatibilit を設定します。|
