---
title: 共通言語ランタイムのアセンブリ
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27a8d89b0345082b8cf06c3eb141e73e2bf0faf
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567364"
---
# <a name="assemblies-in-the-common-language-runtime"></a>共通言語ランタイムのアセンブリ
アセンブリは .NET Framework アプリケーションのビルド ブロックであり、配置、バージョン管理、再利用、アクティブ化のスコープの指定、およびセキュリティ アクセス許可の基本単位となります。 アセンブリは、相互に連携して 1 つの論理的な機能単位を形成するように構築された型やリソースの集合です。 共通言語ランタイムは、型の実装に関して必要な情報をアセンブリから取得します。 共通言語ランタイムにとって、型はアセンブリのコンテキストの外部には存在しません。  
  
 アセンブリの機能は次のとおりです。  
  
- 共通言語ランタイムが実行するコードを保持します。 ポータブル実行可能 (PE: Portable Executable) ファイル内の MSIL (Microsoft Intermediate Language) コードにアセンブリ マニフェストが関連付けられていない場合、このコードは実行されません。 各アセンブリが保持できるエントリ ポイントは 1 つだけです (つまり、`DllMain`、`WinMain`、または `Main`)。  
  
- セキュリティの境界を形成します。 アクセス許可の要求および付与は、アセンブリを単位として行われます。 アセンブリに適用されるセキュリティ境界の詳細については、「[アセンブリのセキュリティに関する考慮事項](../../../docs/framework/app-domains/assembly-security-considerations.md)」を参照してください。  
  
- 型の境界を形成します。 すべての型の ID には、その型を含んでいるアセンブリの名前が含まれます。 したがって、あるアセンブリのスコープに読み込まれた `MyType` と呼ばれる型は、別のアセンブリのスコープに読み込まれた `MyType` と呼ばれる型とは異なります。  
  
- 参照スコープの境界を形成します。 アセンブリのマニフェストには、型を解決したり、リソース要求に応答したりするために使用されるアセンブリ メタデータが含まれています。 このメタデータは、アセンブリの外部に公開する型およびリソースを指定します。 マニフェストには、そのアセンブリが依存するほかのアセンブリも列挙されています。  
  
- バージョンの境界を形成します。 アセンブリは、共通言語ランタイムにおけるバージョン管理の最小単位です。同じアセンブリ内のすべての型およびリソースは、まとめてバージョン管理されます。 アセンブリのマニフェストには、任意の依存アセンブリに対して指定した、バージョンの依存関係が記述されています。 バージョン管理の詳細については、「[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)」を参照してください。  
  
- 配置を行う場合の単位として機能します。 アプリケーションの起動時には、そのアプリケーションが最初に呼び出すアセンブリだけが必要です。 その他のアセンブリ、たとえばローカリゼーション リソースや、ユーティリティ クラスを格納するアセンブリは必要に応じて取得できます。 これにより、最初にダウンロードされるアプリケーションを単純化し、サイズを縮小できます。 アセンブリの配置の詳細については、「[アプリケーションの配置](../../../docs/framework/deployment/index.md)」を参照してください。  
  
- side-by-side 実行がサポートされる場合、その単位として機能します。 同じアセンブリの複数バージョンの同時実行については、「[アセンブリと side-by-side 実行](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)」を参照してください。  
  
 アセンブリには、静的アセンブリと動的アセンブリの 2 種類があります。 静的アセンブリには、.NET Framework の各型 (インターフェイスおよびクラス) と、アセンブリ用のリソース (ビットマップ、JPEG ファイル、リソース ファイルなど) を格納できます。 静的アセンブリは、ディスク上のポータブル実行可能 (PE) ファイルに保存されます。 .NET Framework を使用して動的アセンブリを作成することもできます。動的アセンブリはメモリから直接実行され、実行前にディスクに保存されることはありません。 動的アセンブリは、実行後にディスクに保存できます。  
  
 アセンブリを作成するには、いくつかの方法があります。 Visual Studio など、これまで .dll ファイルや .exe ファイルの作成に使用してきた開発ツールを使用できます。 他の開発環境で作成されたモジュールを使ってアセンブリを作成するには、Windows SDK に付属している各種ツールを使用できます。 動的アセンブリの作成には、<xref:System.Reflection.Emit?displayProperty=nameWithType> などの共通言語ランタイム API も使用できます。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[アセンブリの内容](../../../docs/framework/app-domains/assembly-contents.md)|アセンブリを構成する要素について説明します。|  
|[アセンブリ マニフェスト](../../../docs/framework/app-domains/assembly-manifest.md)|アセンブリ マニフェストのデータについて説明し、データをアセンブリに格納する方法について説明します。|  
|[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)|グローバル アセンブリ キャッシュと、そのキャッシュをアセンブリがどのように使用するかを説明します。|  
|[厳密な名前付きアセンブリ](../../../docs/framework/app-domains/strong-named-assemblies.md)|厳密な名前付きアセンブリの特性について説明します。|  
|[アセンブリのセキュリティに関する考慮事項](../../../docs/framework/app-domains/assembly-security-considerations.md)|セキュリティがアセンブリに対してどのように作用するかを説明します。|  
|[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)|.NET Framework のバージョン管理ポリシーの概要を説明します。|  
|[アセンブリの配置](../../../docs/framework/app-domains/assembly-placement.md)|アセンブリの配置場所について説明します。|  
|[アセンブリと side-by-side 実行](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|複数のバージョンのランタイムやアセンブリの同時使用の概要について説明します。|  
|[アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)|アセンブリを作成し、署名し、その属性を設定する方法を説明します。|  
|[動的メソッドおよびアセンブリの出力](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|動的アセンブリの作成方法を説明します。|  
|[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|実行時に .NET Framework でアセンブリ参照がどのように解決されるかについて説明します。|  
  
## <a name="reference"></a>関連項目  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
