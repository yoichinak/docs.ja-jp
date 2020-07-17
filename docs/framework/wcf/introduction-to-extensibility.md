---
title: 拡張機能の概要
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: ae820e88a790aeaad7c57cde2db84b8168f273a9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321050"
---
# <a name="introduction-to-extensibility"></a>拡張機能の概要
Windows Communication Foundation (WCF) アプリケーションモデルは、分散アプリケーションの通信要件の大部分を解決するように設計されています。 ただし、既定のアプリケーション モデルとシステム提供の実装でサポートされないシナリオが必ず存在します。 WCF の機能拡張モデルは、アプリケーションモデル全体を置き換えるポイントであっても、あらゆるレベルでシステムの動作を変更できるようにすることで、カスタムシナリオをサポートすることを目的としています。 ここでは、拡張のさまざまな領域を提示し、各領域の詳細について説明します。  
  
## <a name="areas-to-extend"></a>拡張する領域  
 次の領域を拡張できます。  
  
- アプリケーション ランタイム。 ここでは、アプリケーションについて、メッセージのディスパッチと処理を拡張します。 この領域には、セキュリティ システム、メタデータ システム、シリアル化システム、およびアプリケーションを基になるチャネル システムに接続するためのバインディングとバインド要素も含まれます。  
  
- チャネルとチャネル ランタイム。 ここでは、メッセージ レベルで機能するシステムを拡張し、プロトコル、トランスポート、およびエンコーディングのサポートを提供します。  
  
- ホスト ランタイム。 ここでは、チャネルおよびアプリケーション ランタイムとのホスト アプリケーション ドメインの関係を拡張します。  
  
### <a name="extending-the-application-runtime"></a>アプリケーション ランタイムの拡張  
 WCF アプリケーションでは、対応するチャネル宛てのメッセージと、アプリケーション自体宛てのメッセージが区別されます。 チャネル メッセージは、セキュリティで保護されたメッセージ交換の確立や、信頼できるセッションの確立など、特定のチャネル関連の機能をサポートします。 このメッセージは、アプリケーション ランタイムでは使用できません。このメッセージは、アプリケーション層が関係する前に処理されます。  
  
 アプリケーション メッセージは、ユーザーまたはユーザーの顧客が作成したクライアントまたはサービスの操作向けのデータを含んでいます。 このメッセージは、必要に応じて、メッセージまたはオブジェクトの形でアプリケーション レベルの拡張システムで使用できます。  
  
 すべてのメッセージはチャネル システムを通過しますが、アプリケーション メッセージだけがチャネル システムからアプリケーションに渡されます。 新しいチャネル レベルの機能を作成するには、チャネル システムを拡張する必要があります。 新しいアプリケーション レベルの機能を作成するには、サービスまたはクライアントのランタイム (それぞれディスパッチャーとチャネル ファクトリ) を拡張する必要があります。 アプリケーションランタイムの拡張の詳細については、「 [ServiceHost とサービスモデルレイヤーの拡張](./extending/extending-servicehost-and-the-service-model-layer.md)」を参照してください。  
  
#### <a name="extending-security"></a>セキュリティの拡張  
 トークンや資格情報などのカスタム セキュリティ機構を作成するには、セキュリティ システムを拡張する必要があります。 詳細については、「[セキュリティの拡張](./extending/extending-security.md)」を参照してください。  
  
#### <a name="extending-metadata"></a>メタデータの拡張  
 メタデータを既定以外の方法で公開するには、メタデータ システムを拡張する必要があります。 詳細については、「[メタデータシステムの拡張](./extending/extending-the-metadata-system.md)」を参照してください。  
  
#### <a name="extending-serialization"></a>シリアル化の拡張  
 カスタム エンコーダーの作成、データ サロゲートの提供、または転送されるデータのカスタマイズに関するその他の作業を行うには、シリアル化システムを拡張する必要があります。 詳細については、「[エンコーダーとシリアライザーの拡張](./extending/extending-encoders-and-serializers.md)」を参照してください。  
  
#### <a name="extending-bindings"></a>バインディングの拡張  
 トランスポート チャネルまたはプロトコル チャネルをアプリケーション層に関連付けるには、バインディング システムを拡張する必要があります。 詳細については、「[バインディングの拡張](./extending/extending-bindings.md)」を参照してください。  
  
### <a name="extending-the-channel-system"></a>チャネル システムの拡張  
 カスタムトランスポートまたはプロトコル機能をサポートするチャネルを作成するには、「[チャネルレイヤーの拡張](./extending/extending-the-channel-layer.md)」を参照してください。  
  
### <a name="extending-the-service-hosting-system"></a>サービス ホスト システムの拡張  
 サービス全体のアプリケーション モデルを変更するには、<xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> クラスを拡張する必要があります。 詳細については、「 [ServiceHost とサービスモデルレイヤーの拡張](./extending/extending-servicehost-and-the-service-model-layer.md)」を参照してください。  
  
 ホスト アプリケーション ドメインとサービス ホストとの関係を変更するには、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> クラスを拡張する必要があります。 詳細については、「 [ServiceHostFactory を使用したホストの拡張](./extending/extending-hosting-using-servicehostfactory.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WCF の拡張](./extending/index.md)
