---
title: '方法: 署名 (WCF) を確認するために使用する証明機関証明書チェーンを指定します。'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 43296fad9519a08db5facdd220492ac70dffeca2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224483"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>方法: 署名 (WCF) を確認するために使用する証明機関証明書チェーンを指定します。
Windows Communication Foundation (WCF) では、X.509 証明書を使用して署名された SOAP メッセージを受信したときに既定ではことを確認、X.509 証明書が信頼された証明機関によって発行されたことです。 これは、証明書ストアを検索し、その証明機関の証明書が信頼された証明書として指定されているかどうかを確認することによって行われます。 WCF この判断を行うためには、適切な証明書ストアに証明機関の証明書チェーンをインストールする必要があります。  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>証明機関証明書チェーンをインストールするには  
  
-   各 SOAP メッセージの受信者によって信頼される証明機関から X.509 証明書を取得する、WCF が構成されている証明書ストアに証明機関の証明書チェーンをインストール、発行された X.509 証明書。  
  
     たとえば、SOAP メッセージの受信者は、マイクロソフトによって発行された X.509 証明書を信頼するが場合の Microsoft 証明機関の証明書チェーンを WCF が X.509 証明書の検索に設定されている証明書ストアにインストールする必要があります。 コードまたは構成では、WCF が X.509 証明書を検索する場合に、証明書ストアを指定できます。 これを指定してコードを使用してなど、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>メソッドまたは構成など、いくつかの点で、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)します。  
  
     Windows には、信頼された証明機関の既定の証明書チェーンのセットが用意されているため、一部の CA については証明書チェーンをインストールする必要はありません。  
  
    1.  証明機関証明書チェーンをエクスポートします。  
  
         正確なエクスポート方法は、証明機関によって異なります。 証明機関で Microsoft 証明書サービスが実行されている場合は、選択**CA 証明書、証明書チェーン、または CRL のダウンロード**を選び、**ダウンロードの CA 証明書**します。  
  
    2.  証明機関証明書チェーンをインポートします。  
  
         Microsoft 管理コンソール (MMC: Microsoft Management Console) で、証明書スナップインを開きます。 選択から X.509 証明書を取得する証明書ストアにその WCF が構成されている、**信頼されたルート** **証明機関**フォルダー。 下、**信頼されたルート証明機関**フォルダーを右クリックし、**証明書**フォルダーを指す**すべてのタスク**、順にクリックします**インポート**. 手順 a. でエクスポートしたファイルを指定します。  
  
         詳細については、MMC で証明書スナップインを使用して、次を参照してください。[方法。MMC スナップインで証明書を表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)します。  
  
## <a name="see-also"></a>関連項目

- [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
