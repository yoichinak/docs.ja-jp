---
title: HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: dcde7bb4cc193d18737d26facbbd69ccd597d66b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599335"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点
Windows Communication Foundation (WCF) の証明書は、トランスポート層セキュリティ (TLS) over HTTP (HTTPS) または TCP に加えて、メッセージ層 (SOAP) セキュリティと共に使用できます。 ここでは、このような証明書の検証方法の違いについて説明します。  
  
## <a name="validation-of-https-client-certificates"></a>HTTPS クライアント証明書の検証  
 HTTPS を使用してクライアントとサービス間で通信を行う場合、サービスに対して認証を行うためにクライアントが使用する証明書はチェーン信頼をサポートしている必要があります。 つまり、信頼されたルート証明機関にチェーンされている必要があります。 それ以外の場合は、HTTP 層によってが発生し、 <xref:System.Net.WebException> "リモートサーバーがエラーを返しました: (403) 許可されていません" というメッセージが表示されます。 WCF は、この例外をとして公開 <xref:System.ServiceModel.Security.MessageSecurityException> します。  
  
## <a name="validation-of-https-service-certificates"></a>HTTP サービス証明書の検証  
 HTTPS を使用してクライアントとサービス間で通信を行う場合、サーバーが認証に使用する証明書は既定でチェーン信頼をサポートしている必要があります。 つまり、信頼されたルート証明機関にチェーンされている必要があります。 証明書が失効しているかどうかを確認するためのオンライン チェックは行われません。 この動作は、<xref:System.Net.Security.RemoteCertificateValidationCallback> コールバックを登録することによってオーバーライドできます。コードは次のようになります。  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 `ValidateServerCertificate` の署名は次のようになります。  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 `ValidateServerCertificate` を実装すると、サービス証明書を検証するために必要であるとクライアント アプリケーションの開発者が考える、すべてのチェックを実行できます。  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>SSL over TCP または SOAP セキュリティにおけるクライアント証明書の検証  
 SSL (Secure Sockets Layer) over TCP またはメッセージ (SOAP) セキュリティを使用する場合、クライアント証明書は <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> プロパティ値に従って検証されます。 プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。 失効チェックは <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> プロパティの値に応じて実行されます。 プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>SSL over TCP および SOAP セキュリティにおけるサービス証明書の検証  
 SSL over TCP またはメッセージ (SOAP) セキュリティを使用する場合、サービス証明書は <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> プロパティ値に従って検証されます。 プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。  
  
 失効チェックは <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> プロパティの値に応じて実行されます。 プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [証明書の使用](working-with-certificates.md)
