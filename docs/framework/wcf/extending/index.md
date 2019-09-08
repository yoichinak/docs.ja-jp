---
title: WCF の拡張
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 037182a3cb105f544e15a05f955c142ba57f62f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795541"
---
# <a name="extending-wcf"></a>WCF の拡張
Windows Communication Foundation (WCF) を使用すると、実行時コンポーネントを変更および拡張して、サービスベースのアプリケーションを正確に制御および拡張することができます。 このセクションのトピックでは、その拡張アーキテクチャについて詳しく説明します。 基本的なプログラミングの詳細については、「[基本的な WCF プログラミング](../basic-wcf-programming.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ServiceHost とサービス モデル レイヤーの拡張](extending-servicehost-and-the-service-model-layer.md)  
 サービス モデル レイヤーには、基になるチャネルから受信メッセージを取得し、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信するという役割があります。  サービス モデル拡張は、ディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。  
  
 [バインディングの拡張](extending-bindings.md)  
 バインディングはエンドポイントに接続するために必要な通信の詳細設定を記述するオブジェクトです。 バインディングの拡張やカスタム バインドは、アプリケーションの各種機能をサポートするために必要なカスタム通信機能を実装します。  
  
 [チャネル レイヤーの拡張](extending-the-channel-layer.md)  
 チャネル レイヤーは、サービス モデル レイヤーより下に位置し、クライアントとサービス間のメッセージの交換を担います。 チャネル拡張は、セキュリティなどの新しいプロトコル機能を実装できます。 また、SOAP メッセージを伝達する新しいネットワーク トランスポートの実装など、トランスポート機能も実装できます。  
  
 [セキュリティの拡張](extending-security.md)  
 WCF のセキュリティは、転送セキュリティ (整合性、機密性、および認証)、アクセス制御 (承認)、および監査で構成されます。 `IdentityModel`名前空間で見つかったクラスは、アクセス制御のために WCF によって使用されます。 セキュリティ アーキテクチャを理解することによって、カスタムのアクセス制御システムに対応したカスタムのクレーム タイプを作成できます。  
  
 [メタデータ システムの拡張](extending-the-metadata-system.md)  
 WCF メタデータシステムは、サービスベースのアプリケーションを実装するために必要なメタデータを表すクラスとインターフェイスのグループです。 クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。  
  
 [エンコーダーとシリアライザーの拡張](extending-encoders-and-serializers.md)  
 エンコーダーとシリアライザーは、データをある形式から別の形式に変換します。 このセクションのトピックでは、提供されたクラスを特別な要件に合わせて拡張する方法を説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>関連項目  
 [基本的な WCF プログラミング](../basic-wcf-programming.md)  
  
 [WCF 機能の詳細](../feature-details/index.md)  
  
 [ガイドラインとベスト プラクティス](../guidelines-and-best-practices.md)
