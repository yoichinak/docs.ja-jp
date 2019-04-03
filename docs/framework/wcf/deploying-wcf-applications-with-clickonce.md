---
title: ClickOnce を使用して WCF アプリケーションを展開する
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 91c03ee2fa33541e917e44583c5fa20173aec34e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680976"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>ClickOnce を使用して WCF アプリケーションを展開する
Windows Communication Foundation (WCF) を使用するクライアント アプリケーションは、ClickOnce テクノロジを使用してデプロイできます。 このテクノロジを使用すると、クライアント アプリケーションが、信頼できる証明書でデジタル署名されている場合、コード アクセス セキュリティによって提供されるランタイム セキュリティ保護を受けられます。 ClickOnce アプリケーションの署名に使用される証明書は、信頼された発行者のストアに存在する必要があり、またそのクライアント コンピューターのローカル セキュリティ ポリシーでは、発行者の証明書で署名されたアプリケーションに対して、完全信頼のアクセス許可が構成される必要があります。  
  
 ClickOnce アプリケーションと信頼された発行元を構成する方法の詳細については、[Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [信頼されたアプリケーションの配置の概要](https://go.microsoft.com/fwlink/?LinkId=94775)
- [ClickOnce 配置の Windows フォーム アプリケーション](https://go.microsoft.com/fwlink/?LinkId=94776)
