---
title: .NET リモート処理アプリケーションの WCF への移行
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 4040fb0ac223f91705a49b733f6a1f42d144068e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046607"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET リモート処理アプリケーションの WCF への移行
**このトピックの対象は、既存のアプリケーションとの下位互換性のために残されているレガシ テクノロジに特定されています。新規の開発には、このトピックを適用しないでください。WCF を使用して、分散アプリケーションを開発する必要がありますようになりました。**  
  
 既存の .NET リモート処理アプリケーションと WCF を活用するために 2 つの方法があります。 統合と移行します。 統合では、.NET Remoting 2.0 と WCF を並行して実行されている、既存の .NET Remoting 2.0 コードを変更することがなく同時に両方のテクノロジを同じビジネス オブジェクトを公開することができます。 統合では、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 以降が実行されている必要があります。 WCF の機能を利用して、Remoting 2.0 システムとの互換性を配線する必要はない場合、は、サービス全体を WCF に移行することができます。 .NET Remoting 2.0 から WCF への移行では、リモート オブジェクトのインターフェイスとその構成設定の変更が必要です。 両方のトピックに掲載されて[を Windows Communication Foundation からリモート処理](https://go.microsoft.com/fwlink/?LinkId=74403)します。  
  
## <a name="see-also"></a>関連項目

- [概念](../../../../docs/framework/wcf/conceptual-overview.md)
