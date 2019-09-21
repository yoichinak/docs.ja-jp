---
title: '方法: 証明書を取得する (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: e720a6742506f6270fda65de12f510c2a6224873
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929187"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>方法: 証明書を取得する (WCF)
X.509 証明書を使用するの Windows Communication Foundation (WCF) 機能のいずれかを使用するには、最初に証明書を取得するだけです。  
  
### <a name="to-obtain-an-x509-certificate"></a>X.509 証明書を取得するには  
  
1. 次のいずれかを選択します。  
  
    - VeriSign, Inc. などの証明機関から証明書を購入します。  
  
    - 独自の証明書サービスを設定し、証明機関に証明書への署名を依頼します。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]、Windows 2000 Server、Windows 2000 Server Datacenter、および Windows 2000 Datacenter Server にはすべて、公開キー基盤 (PKI) をサポートする証明書サービスが用意されています。 Windows Server 2008 では、 [Active Directory 証明書サービス](https://go.microsoft.com/fwlink/?LinkID=153483)の役割を使用して、証明機関を管理します。  
  
    - 独自の証明書サービスを設定し、証明書には署名しません。  
  
    > [!NOTE]
    > どの方法を使用する場合でも、X.509 証明書を含む SOAP 要求の受信者は、その X.509 証明書を信頼する必要があります。 つまり、証明書チェーン内の X.509 証明書または発行者は、信頼されたユーザーの証明書ストア内に存在し、また X.509 証明書は信頼されない証明書ストア内には存在しないということを意味します。  
  
## <a name="see-also"></a>関連項目

- [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [方法: 開発時に使用する一時的な証明書を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
