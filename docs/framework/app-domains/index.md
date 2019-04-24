---
title: アプリケーション ドメインとアセンブリを使用したプログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675352"
---
# <a name="programming-with-application-domains-and-assemblies"></a>アプリケーション ドメインとアセンブリを使用したプログラミング
Microsoft Internet Explorer、ASP.NET、Windows シェルなどのホストは、共通言語ランタイムをプロセスに読み込み、そのプロセス内で[アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)を作成します。その後 .NET Framework アプリケーションを実行するときに、そのアプリケーション ドメインにユーザー コードを読み込んでコードを実行します。 通常、アプリケーション ドメインの作成およびそれらのドメインへのアセンブリの読み込みはランタイム ホストが実行するため、考慮する必要はありません。  
  
 しかし、共通言語ランタイムをホストするアプリケーションを作成する場合、プログラムによってアンロードされるツールまたはコードを作成する場合、または実行時にアンロードおよび再読み込みできるプラグ可能なコンポーネントを作成する場合は、独自のアプリケーション ドメインを作成します。 ランタイム ホストを作成しない場合でも、このセクションにある、アプリケーション ドメインとアプリケーション ドメインに読み込まれたアセンブリをどのように使用するかという説明は重要です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アプリケーション ドメインとアセンブリに関する方法のトピック](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 アプリケーション ドメインとアセンブリを使用したプログラミングの概念に関するドキュメントに用意されているすべての方法トピックへのリンクを示します。  
  
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)  
 アプリケーション ドメインを作成、構成、および使用する例を示します。  
  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 アセンブリを作成し、署名し、その属性を設定する方法を説明します。  
  
## <a name="related-sections"></a>関連項目  
 [動的メソッドおよびアセンブリの出力](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 動的アセンブリの作成方法を説明します。  
  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 アセンブリの概念的な概要を説明します。  
  
 [アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)  
 アプリケーション ドメインの概念的な概要を説明します。  
  
 [リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)  
 **Reflection** クラスを使用して、アセンブリに関する情報を取得する方法を説明します。
