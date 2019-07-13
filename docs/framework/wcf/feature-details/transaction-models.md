---
title: トランザクション モデル
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050780"
---
# <a name="transaction-models"></a>トランザクション モデル
ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。  
  
 トランザクションでは、Windows Communication Foundation (WCF) を使用する場合を選択する別のトランザクション モデルですが統合され一貫したモデルのさまざまなレイヤーではなくオペレーティングは理解してください。  
  
 以下に、3 つの主要なトランザクション コンポーネントについて説明します。  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation トランザクション  
 WCF でサポートされるトランザクションは、トランザクション サービスを作成できます。 さらに、WS-AtomicTransaction (WS-AT) プロトコルのサポート、アプリケーションは、WCF またはサード パーティのテクノロジを使用して構築された Web サービスにトランザクションをフローできます。  
  
 WCF サービスまたはアプリケーションでは、WCF トランザクション機能は、属性と宣言によってを指定する方法とタイミング インフラストラクチャが作成フロー、トランザクションを同期の構成を提供します。  
  
## <a name="systemtransactions-transactions"></a>System.Transactions トランザクション  
 <xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。  
  
 これら 2 つのモデルを使用してトランザクション アプリケーションを作成する方法の詳細については、次を参照してください。[トランザクション アプリケーションの作成](https://go.microsoft.com/fwlink/?LinkId=94947)です。  
  
 WCF サービスまたはアプリケーション、<xref:System.Transactions>サービス内で必要なときに、トランザクションに明示的に対話して、クライアント アプリケーション内でトランザクションを作成するために、プログラミング モデルを提供します。  
  
## <a name="msdtc-transactions"></a>MSDTC トランザクション  
 Microsoft 分散トランザクション コーディネーター (MSDTC) は、分散トランザクションをサポートするトランザクション マネージャーです。  
  
 詳細については、次を参照してください。、 [DTC プログラマ リファレンス](https://go.microsoft.com/fwlink/?LinkId=94948)します。  
  
 WCF サービスまたはアプリケーションでは、MSDTC は、クライアントまたはサービス内で作成されたトランザクションの調整のインフラストラクチャを提供します。
