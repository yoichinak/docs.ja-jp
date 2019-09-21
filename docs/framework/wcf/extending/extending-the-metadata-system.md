---
title: メタデータ システムの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: d3ce7e1a228e6303be1009c7b72f4e889b40c536
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795719"
---
# <a name="extending-the-metadata-system"></a>メタデータ システムの拡張
Windows Communication Foundation (WCF) メタデータシステムは、サービスベースのアプリケーションを実装するために必要なメタデータを表すクラスとインターフェイスのグループです。 クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [WCF 拡張に対するカスタム メタデータのエクスポート](exporting-custom-metadata-for-a-wcf-extension.md)  
 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、カスタム ポリシー アサーションを WSDL ドキュメントに埋め込む方法を説明します。  
  
 [WCF 拡張に対するカスタム メタデータのインポート](importing-custom-metadata-for-a-wcf-extension.md)  
 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、WSDL ドキュメント内のカスタム ポリシー アサーションの読み取りや応答を行う方法を説明します。  
  
 [カスタム バインディングを介したメタデータの公開と取得](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 カスタム バインドを介してメタデータを交換する方法について説明します。
