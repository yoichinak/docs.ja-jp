---
title: Trust プロトコルが混在するフェデレーション シナリオ
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 18f486b9de83db48e186bb3856aff6cc6ccb56b1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606506"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Trust プロトコルが混在するフェデレーション シナリオ
シナリオによっては、フェデレーション クライアントが、Trust バージョンの一致しないサービスやセキュリティ トークン サービス (STS: Security Token Service) と通信する場合があります。 たとえば、サービス WSDL に、STS とは異なるバージョンの WS-Trust 要素を持つ `RequestSecurityTokenTemplate` アサーションが含まれることがあります。 このような場合は、Windows Communication Foundation (WCF) クライアントがから受け取った Ws-trust 要素を変換、 `RequestSecurityTokenTemplate` STS trust バージョンの一致するようにします。 WCF では、標準バインディングのみを対象の不一致の trust バージョンを処理します。 WCF によって認識されるすべての標準的なアルゴリズム パラメーターは、標準バインディングの一部です。 このトピックでは、サービスと STS の間さまざまな信頼の設定で WCF の動作について説明します。  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP 2005/02 および STS 2005/02  
 証明書利用者 (RP: Relying Party) の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 WCF は、クライアントとサービスのパラメーターを区別できません。すべてのパラメーターを追加し、で送信、 `RequestSecurityTokenTemplate` (RST)。  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP Trust 1.3 および STS Trust 1.3  
 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParameters` 要素が含まれます。  
  
 WCF の削除、 `EncryptionAlgorithm`、`CanonicalizationAlgorithm`と`KeyWrapAlgorithm`rst 中に存在する場合、最上位の要素から要素、`SecondaryParameters`要素。 WCF の追加、`SecondaryParameters`に変更されていない送信 RST 要素。  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP Trust 2005/02 および STS Trust 1.3  
 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 クライアント構成ファイルから WCF は、サービスとクライアント パラメーターを区別できません。 そのため WCF では、信頼関係のバージョン 1.3 の名前空間にすべてのパラメーターを変換します。  
  
 WCF のハンドル、 `KeyType`、 `KeySize`、および`TokenType`要素として次のとおりです。  
  
- WSDL をダウンロードし、バインディングを作成して、`KeyType`、`KeySize`、および `TokenType` を RP パラメーターから割り当てます。 その後、クライアント構成ファイルが生成されます。  
  
- この時点で、クライアントは構成ファイル内のパラメーターを変更できます。  
  
- WCF 実行時に指定されたすべてのパラメーターがコピー、`AdditionalTokenParameters`以外のクライアント構成ファイルのセクション`KeyType`、`KeySize`と`TokenType`これらのパラメーターは、構成ファイル中に考慮するため、生成します。  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP Trust 1.3 および STS Trust 2005/02  
 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParamters` 要素が含まれます。  
  
 WCF のコピー内で指定されたすべてのパラメーター、`SecondaryParameters`最上位の RST 要素にセクション 2005 Ws-trust 名前空間には変換されません。
