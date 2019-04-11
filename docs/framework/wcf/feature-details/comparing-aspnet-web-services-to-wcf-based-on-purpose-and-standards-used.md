---
title: 使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: f57e895680b5cc043dad365b9f25f32477f42e72
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147408"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較
ASP.NET Web サービスは、HTTP 上で SOAP (Simple Object Access Protocol) を使用してメッセージを送受信するアプリケーションを構築するために開発されました。 メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージのシリアル化を容易にするツールも提供されています。 このテクノロジを使用すると、Web サービス記述言語 (WSDL) で Web サービスを記述するメタデータが自動で生成されます。また、WSDL から Web サービス用のクライアントを生成する別のツールも用意されています。  
  
 WCF では、.NET Framework アプリケーションは、他のソフトウェア エンティティとメッセージ交換を有効にするためです。 既定では SOAP が使用されますが、任意の形式のメッセージを使用でき、任意のトランスポート プロトコルを使用してメッセージを伝達できます。 メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージをシリアル化するさまざまなオプションがあります。 WCF が WSDL でテクノロジを使用して構築されたアプリケーションを記述するメタデータを自動的に生成し、WSDL からこれらのアプリケーション用のクライアントを生成するためのツールも提供します。  
  
 ASP.NET Web サービスでサポートされる標準に記載されて[ASP.NET を使用して作成した XML Web サービス](https://go.microsoft.com/fwlink/?LinkId=94872)します。 WCF でサポートされる標準のより広範な一覧が掲載[システム標準の相互運用性バインディングでサポートされる Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)します。  
  
## <a name="see-also"></a>関連項目

- [開発者の視点から見た ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
