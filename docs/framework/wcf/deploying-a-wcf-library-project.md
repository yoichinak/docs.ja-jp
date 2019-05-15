---
title: WCF ライブラリ プロジェクトの配置
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 0400fc9ec5a5629139348709bbd3a5554ce251c7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593343"
---
# <a name="deploying-a-wcf-library-project"></a>WCF ライブラリ プロジェクトの配置
このトピックでは、Windows Communication Foundation (WCF) サービス ライブラリ プロジェクトをデプロイする方法について説明します。  
  
## <a name="deploying-a-wcf-service-library"></a>WCF サービス ライブラリの配置  
 WCF サービス ライブラリは、ダイナミック リンク ライブラリ (DLL) です。 それ自体を単独で実行することはできません。 ホスティング環境に配置する必要があります。 このプロセスの詳細については、次を参照してください。 [WCF サービスの使用のホスティングと](https://go.microsoft.com/fwlink/?LinkId=99932)します。  
  
 WCF サービス ライブラリは、その他の WCF サービスと同様に展開できます。 ただし、.NET Framework が Dll の構成をサポートしないこともあります。 <xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。 WCF サービス ライブラリ プロジェクトは、開発中に、ライブラリの App.config ファイルを提供することで、この制限を軽減します。 ただし、配置後、この App.config ファイルは認識されません。  
  
 構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。 自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。 サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。
