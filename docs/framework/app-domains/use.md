---
title: アプリケーション ドメインの使用
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674892"
---
# <a name="using-application-domains"></a>アプリケーション ドメインの使用
アプリケーション ドメインには、共通言語ランタイムに使用できる分離の単位が用意されています。 アプリケーション ドメインはプロセス内で作成され、実行されます。 通常、アプリケーション ドメインはランタイム ホストによって作成されます。ランタイム ホストは、ランタイムをプロセスに読み込み、アプリケーション ドメイン内でユーザー コードを実行する処理を担当します。 ランタイム ホストはプロセスと既定のアプリケーション ドメインを作成し、その中でマネージド コードを実行します。 ランタイム ホストには、ASP.NET、Microsoft Internet Explorer、Windows シェルなどがあります。  
  
 ほとんどのアプリケーションでは、独自のアプリケーション ドメインを作成する必要はありません。必要なアプリケーション ドメインがあれば、ランタイム ホストで自動的に作成されます。 ただし、アプリケーションでコードを分離する必要がある場合や、DLL を使用してアンロードする必要がある場合は、追加のアプリケーション ドメインを作成して構成する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: アプリケーション ドメインを作成する](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 プログラムでアプリケーション ドメインを作成する方法について説明します。  
  
 [方法: アプリケーション ドメインをアンロードする](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 プログラムでアプリケーション ドメインをアンロードする方法について説明します。  
  
 [方法: アプリケーション ドメインを構成する](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 アプリケーション ドメインの構成方法の概要を説明します。  
  
 [アプリケーション ドメインからのセットアップ情報の取得](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 アプリケーション ドメインからセットアップ情報を取得する方法について説明します。  
  
 [方法: アプリケーション ドメインにアセンブリを読み込む](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 アセンブリをアプリケーション ドメインに読み込む方法について説明します。  
  
 [方法: アセンブリから型およびメンバーの情報を取得する](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 アセンブリに関する情報を取得する方法について説明します。  
  
 [アセンブリのシャドウ コピー](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 シャドウ コピーによってアセンブリの使用中に更新する方法と、シャドウ コピーを構成する方法について説明します。  
  
 [方法: 初回例外通知を受け取る](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 共通言語ランタイムが例外ハンドラーの検索を開始する前に、例外がスローされたことを知らせる通知を受け取る方法について説明します。  
  
 [アセンブリ読み込みの解決](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> イベントを使用してアセンブリの読み込みエラーを解決する方法について説明します。  
  
## <a name="reference"></a>関連項目  
 <xref:System.AppDomain>  
 アプリケーション ドメインを表現します。 アプリケーション ドメインの作成と制御に使用するメソッドについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 アセンブリで実行される関数の概要について説明します。  
  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 アセンブリを作成し、署名し、その属性を設定する方法を説明します。  
  
 [動的メソッドおよびアセンブリの出力](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 動的アセンブリの作成方法を説明します。  
  
 [アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)  
 アプリケーション ドメインの概念的な概要を説明します。  
  
 [リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)  
 **Reflection** クラスを使用して、アセンブリに関する情報を取得する方法を説明します。
