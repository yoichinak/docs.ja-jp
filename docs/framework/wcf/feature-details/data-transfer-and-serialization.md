---
title: データ転送とシリアル化
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 1eefd82a149d0bc215ca441e92c7d737a744b1e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088406"
---
# <a name="data-transfer-and-serialization"></a>データ転送とシリアル化
接続されたシステムでは、サービスとクライアントのタスクの実行は、データの交換に依存します。 サービスまたはクライアントの開発者は、効率的かつ簡単に維持されるアプリケーションを作成するには、Windows Communication Foundation (WCF) がデータとデータのシリアル化を処理する方法も理解する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [サービス コントラクトでのデータ転送の指定](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 サービスでのデータ転送の基本的な概念について説明します。  
  
 [データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 データ コントラクトの定義と、その作成方法と使用方法について説明します。  
  
 [データ コントラクト シリアライザー](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <xref:System.Runtime.Serialization.DataContractSerializer> クラス、または <xref:System.Runtime.Serialization.XmlObjectSerializer> クラスの拡張機能で、データのシリアル化を実行する方法について説明します。  
  
 [XmlSerializer クラスの使用](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <xref:System.Xml.Serialization.XmlSerializer> クラスの代わりに、<xref:System.Runtime.Serialization.DataContractSerializer> クラスを使う方法とその理由について説明します。  
  
 [メッセージ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 メッセージ コントラクトで SOAP メッセージを詳細に制御する方法について説明します。  
  
 [メッセージ クラスの使用](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 メッセージ クラス機能の使用方法について説明します。  
  
 [フィルター処理](../../../../docs/framework/wcf/feature-details/filtering.md)  
 各種の条件に基づいて、メッセージを事前処理できるフィルター処理について説明します。  
  
 [大規模データとストリーミング](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 バイナリ ファイルなど、大きなデータ ブロックを送信する方法について説明します。  
  
 [セキュリティに関するデータの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 データの転送とシリアル化をプログラムするときに注意する必要のある項目について説明します。  
  
 [データ転送のアーキテクチャの概要](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 WCF でのデータ転送の設計全体のビューについて説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>関連項目  
 [エンコーダーとシリアライザーの拡張](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>関連項目

- [ベスト プラクティス:データ コントラクトのバージョン管理](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [サービスのバージョン管理](../../../../docs/framework/wcf/service-versioning.md)
