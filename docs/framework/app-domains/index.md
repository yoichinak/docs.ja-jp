---
title: アプリケーション ドメインとアセンブリを使用したプログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 3f66eacaf30f8001cdbf3a486e5ce1c878712e2f
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644273"
---
# <a name="programming-with-application-domains-and-assemblies"></a>アプリケーション ドメインとアセンブリを使用したプログラミング

Microsoft Internet Explorer、ASP.NET、Windows シェルなどのホストは、共通言語ランタイムをプロセスに読み込み、そのプロセス内で[アプリケーション ドメイン](application-domains.md)を作成します。その後 .NET Framework アプリケーションを実行するときに、そのアプリケーション ドメインにユーザー コードを読み込んでコードを実行します。 通常、アプリケーション ドメインの作成およびそれらのドメインへのアセンブリの読み込みはランタイム ホストが実行するため、考慮する必要はありません。  
  
しかし、共通言語ランタイムをホストするアプリケーションを作成する場合、プログラムによってアンロードされるツールまたはコードを作成する場合、または実行時にアンロードおよび再読み込みできるプラグ可能なコンポーネントを作成する場合は、独自のアプリケーション ドメインを作成します。 ランタイム ホストを作成しない場合でも、このセクションにある、アプリケーション ドメインとアプリケーション ドメインに読み込まれたアセンブリをどのように使用するかという説明は重要です。  
  
## <a name="in-this-section"></a>このセクションの内容  

[アプリケーション ドメインとアセンブリに関する方法のトピック](application-domains-and-assemblies-how-to-topics.md)  
アプリケーション ドメインとアセンブリを使用したプログラミングの概念に関するドキュメントに用意されているすべての方法トピックへのリンクを示します。  
  
[アプリケーション ドメインの使用](use.md)  
アプリケーション ドメインを作成、構成、および使用する例を示します。  
  
[アセンブリを使用したプログラミング](../../standard/assembly/index.md)  
アセンブリを作成し、署名し、その属性を設定する方法を説明します。  
  
## <a name="related-sections"></a>関連項目  

[動的メソッドおよびアセンブリの出力](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
動的アセンブリの作成方法を説明します。  
  
[.NET のアセンブリ](../../standard/assembly/index.md)  
アセンブリの概念的な概要を説明します。  
  
[アプリケーション ドメイン](application-domains.md)  
アプリケーション ドメインの概念的な概要を説明します。  
  
[リフレクションの概要](../reflection-and-codedom/reflection.md)  
**Reflection** クラスを使用して、アセンブリに関する情報を取得する方法を説明します。
