---
title: "信頼性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3329bff14d2ab395fecfde0f26942b7cb1b9640e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="reliability"></a>信頼性
SQL Server などのサーバー環境で実行するコードは、非同期例外から保護することが重要です。 ここで説明するように、信頼性とは、SQL Server に限ったことではなく、.NET Framework バージョン 2.0 の環境で実行するホスト用に信頼性の高いコードを書くことです。 ただし、SQL Server はバージョン 2.0 の新しい信頼性機能を広範に使う初めてのサービスなので、例として使います。  
  
 SQL Server で実行されるコードは、他のサーバー環境より厳格な信頼性ガイドラインに対応する必要があります。 これは、リソース消費での SQL Server の安定した動作のためです。  <xref:System.OutOfMemoryException> および <xref:System.Threading.ThreadAbortException> 例外は、SQL Server 環境では珍しくありません。 一般に、これらのガイドラインでの主眼は、信頼性より、<xref:System.AppDomain> レベルのリサイクルが発生したときに完全に信頼されたマネージ コードが正常に失敗できるようにすることにあります。リサイクルは、サーバーが整合性と可用性を維持する主要な手段です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server プログラミングとホスト保護属性](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 SQL Server が <xref:System.Security.Permissions.HostProtectionAttribute> 属性を使ってマネージ コードの実行を制限する方法について説明します。  
  
 [信頼性に関するベスト プラクティス](../../../docs/framework/performance/reliability-best-practices.md)  
 信頼性の要件を満たすコードを記述するためのガイドラインを提供します。  
  
 [制約された実行領域](../../../docs/framework/performance/constrained-execution-regions.md)  
 制約された実行領域 (CER) の機能と動作について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
