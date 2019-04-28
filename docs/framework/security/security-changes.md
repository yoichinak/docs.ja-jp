---
title: .NET Framework におけるセキュリティの変更点
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c62a469b3e31283e5790c747092a8fe504ef8c2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670151"
---
# <a name="security-changes-in-the-net-framework"></a>.NET Framework におけるセキュリティの変更点
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] のセキュリティにおける最も重要な変更は、厳密な名前付けの変更です。 これらの変更の詳細については、「 [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) 」を参照してください。  
  
 .NET Framework は、マネージド アプリケーションに 2 階層のセキュリティ モデルを提供します。 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリはリソースへのアクセスを制限する Windows セキュリティ コンテナーで実行されます。 そのコンテナー内では、マネージド アプリケーションは完全に信頼された状態で実行します。 コード アクセス セキュリティの (CAS) の観点からは、権限を昇格するために開発者が実行できる操作はありません。 Windows で与えられる権限の詳細については、Windows デベロッパー センターの「 [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) 」 (アプリの機能宣言 (Windows ストア アプリ)) を参照してください。 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの作成については、「 [C# または Visual Basic を使った初めての Windows ストア アプリの作成](https://go.microsoft.com/fwlink/?LinkId=230461)」を参照してください。
