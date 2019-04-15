---
title: '方法: 一貫性を保って X.509 証明書を参照する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: bd911b1586f7f4a4816efa32480ef99ca12404f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176203"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>方法: 一貫性を保って X.509 証明書を参照する
証明書を識別する方法には、証明書のハッシュを使用する方法、発行者とシリアル番号を使用する方法、またはサブジェクト キー識別子 (SKI) を使用する方法があります。 SKI を使用すると、証明書のサブジェクト公開キーを一意に識別できます。SKI は、XML デジタル署名を処理する場合によく使用されます。 SKI の値は、X.509 証明書形式の一部では通常、 *X.509 証明書の拡張*します。 Windows Communication Foundation (WCF) は、既定値を持つ*参照スタイル*SKI 拡張が証明書に見つからない場合は、発行者とシリアル番号を使用します。 証明書に SKI 拡張が含まれる場合、既定の参照スタイルは SKI を使用してその証明書を識別します。 場合、アプリケーションの開発を途中から SKI 拡張を使用する証明書に SKI 拡張を使用しない証明書を使用して切り替えることが、WCF で生成されたメッセージで使用される参照スタイルも変更します。  
  
 SKI 拡張が存在するかどうかに関係なく、一貫性のある参照スタイルが必要な場合は、次のコードに示されているような参照スタイルを構成できます。  
  
## <a name="example"></a>例  
 次の例では、1 つの一貫した参照スタイル (ユーザー名とシリアル番号) を使用するカスタム セキュリティ バインド要素を作成します。  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードのコンパイルには次の名前空間が必要です。  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>関連項目

- [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
