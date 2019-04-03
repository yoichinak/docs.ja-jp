---
title: WCF ライブラリ プロジェクトの配置
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 1ba26a7e68fe262dc5f4f569647af1ebb94e03a8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042531"
---
# <a name="deploying-a-wcf-library-project"></a>WCF ライブラリ プロジェクトの配置
このトピックでは、Windows Communication Foundation (WCF) サービス ライブラリ プロジェクトをデプロイする方法について説明します。  
  
## <a name="deploying-a-wcf-service-library"></a>WCF サービス ライブラリの配置  
 WCF サービス ライブラリは、ダイナミック リンク ライブラリ (DLL) です。 それ自体を単独で実行することはできません。 ホスティング環境に配置する必要があります。 このプロセスの詳細については、[WCF サービスの使用のホスティングと](https://go.microsoft.com/fwlink/?LinkId=99932)を参照してください。  
  
 WCF サービス ライブラリは、その他の WCF サービスと同様に展開できます。 ただし、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、DLL に対する構成がサポートされていないことに注意してください。 <xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。 WCF サービス ライブラリ プロジェクトは、開発中に、ライブラリの App.config ファイルを提供することで、この制限を軽減します。 ただし、配置後、この App.config ファイルは認識されません。  
  
 構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。 自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。 サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。
