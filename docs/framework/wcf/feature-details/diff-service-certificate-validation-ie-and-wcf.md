---
title: Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225920"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
Internet Explorer と Windows Communication Foundation (WCF) HTTPS を使用するときにサービス証明書の検証方法の違いのためなっても、Internet Explorer は、ヘルプ ページまたは Web サービス記述言語にアクセスできません。(WSDL)、サービスの WCF クライアントが正常にできる場合でもメッセージ、サービス エンドポイントに送信します。 これは Internet Explorer のチェックがあるため、サービス証明書があるかどうか、 `ServerAuthentication` WCF では、このような制約は強制されませんが、オブジェクト識別子 (OID) の拡張使用法フラグ。 Internet Explorer がサービス ヘルプ ページまたはサービスの WSDL にアクセスできない場合は、使用、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータにアクセスします。  
  
## <a name="see-also"></a>関連項目

- [HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [方法: メタデータの取得および準拠サービスの実装](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
