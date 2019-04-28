---
title: Windows Communication Foundation バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: e69cd500c50e9d76824d0e438a1af86f3a722c52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857689"
---
# <a name="windows-communication-foundation-bindings"></a>Windows Communication Foundation バインディング
Windows Communication Foundation (WCF) では、その他のソフトウェアと通信する方法からアプリケーション用のソフトウェアを記述する方法を分離します。 バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定します。 WCF では、バインドを使用して、バインディングの詳細のほとんどは通信しているパーティ間で合意する必要がありますので、エンドポイントの基になるネットワーク表現を生成します。 これを実現する最も簡単な方法は、サービスのクライアントがサービスのエンドポイントと同じバインディングを使用することです。 これを行う方法の詳細については、次を参照してください。[サービスを構成してクライアントを使用してバインド](~/docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)します。  
  
 バインディングは、バインド要素のコレクションで構成されます。 各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。 バインディングには、1 つ以上のトランスポート バインド要素、1 つ以上のメッセージ エンコーディング バインド要素 (既定では、トランスポート バインド要素によって提供されます)、および任意の数の他のプロトコル バインド要素が含まれている必要があります。 このように、ランタイムをビルドするプロセスでは、各バインド要素からランタイムにコードを提供できます。  
  
 WCF には、バインド要素の一般的な選択内容が含まれているバインドが用意されています。 これらのバインディングは、既定の設定で使用することも、ユーザーの要件に応じて既定値を変更することもできます。 これらのシステム指定のバインディングには、バインド要素およびその設定を直接制御できるプロパティが含まれます。 また、バインディングの各バージョンに独自の名前を付けることで、複数のバージョンを同時に使用することもできます。 詳細については、次を参照してください。 [Configuring System-Provided バインド](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)します。  
  
 システム指定のバインディングに用意されていないバインド要素のコレクションが必要になった場合には、その必要なバインド要素のコレクションで構成されるカスタム バインドを作成できます。 このようなカスタム バインドは簡単に作成でき、新しいクラスも必要ありませんが、バインド要素およびその設定を制御するためのプロパティは提供されません。 バインド要素へのアクセスと設定の変更は、バインド要素を含むコレクションを通じて行います。 詳細については、次を参照してください。[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [システムが提供するバインディングの構成](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 使用して、一般的なシナリオをサポートするために WCF が提供するバインドを変更する方法について説明します。  
  
 [サービスとクライアントを構成するためのバインディングの使用](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 コードと構成を使用して宣言で強制的にサービスとクライアントの Windows Communication Foundation (WCF) バインドを定義する方法について説明します。  
  
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 <xref:System.ServiceModel.Channels.CustomBinding> の概要と使用する状況について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>関連項目  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)
