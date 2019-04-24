---
title: アセンブリの場所
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c638531bd54f14c7e4b04a093deaec729db404ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129637"
---
# <a name="assembly-location"></a>アセンブリの場所
アセンブリの場所は、参照時に共通言語ランタイムがそれを見つけることができるかどうかを決定します。また、アセンブリをその他のアセンブリと共有できるかどうかも決定できます。 次の場所にアセンブリを展開することができます。  
  
-   アプリケーションのディレクトリまたはサブディレクトリ  
  
     これは、アセンブリを展開する最も一般的な場所です。 アプリケーションのルート ディレクトリのサブディレクトリは、言語またはカルチャを基にすることができます。 アセンブリにカルチャ属性の情報がある場合は、アプリケーション ディレクトリの下のサブディレクトリに、そのカルチャの名前で存在する必要があります。  
  
-   グローバル アセンブリ キャッシュ  
  
     これは、共通言語ランタイムをインストールしている場所にインストールされている、コンピューター全体で使用できるコード キャッシュです。 ほとんどの場合、あるアセンブリを複数のアプリケーションで共有する場合は、そのアセンブリをグローバル アセンブリ キャッシュ内に展開する必要があります。  
  
-   HTTP サーバー上  
  
     HTTP サーバーに展開されているアセンブリは、厳密な名前を持つ必要があります。アプリケーションの構成ファイルのコードベース セクションにあるアセンブリをポイントします。  
  
## <a name="see-also"></a>関連項目

- [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)
- [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)
- [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
