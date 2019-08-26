---
title: アセンブリを使用したプログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921433"
---
# <a name="programming-with-assemblies"></a>アセンブリを使用したプログラミング
アセンブリは .NET Framework の構成要素であり、配置、バージョン管理、再利用、アクティブ化のスコープの指定、およびセキュリティ アクセス許可の基本単位となります。 共通言語ランタイムは、型の実装に関して必要な情報をアセンブリから取得します。 アセンブリは、相互に連携して 1 つの論理的な機能単位を形成するように構築された型やリソースの集合です。 共通言語ランタイムにとって、型はアセンブリのコンテキストの外部には存在しません。  
  
 このセクションでは、モジュールを作成する方法、モジュールからアセンブリを作成する方法、キー ペアを作成して厳密な名前でアセンブリに署名する方法、およびグローバル アセンブリ キャッシュにアセンブリをインストールする方法について説明します。 さらに、[MSIL 逆アセンブラー (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使ってアセンブリ マニフェストの情報を表示する方法も説明します。  
  
> [!NOTE]
> .NET Framework Version 2.0 以降では、現在読み込まれているランタイムよりもバージョン番号が新しい .NET Framework のバージョンでコンパイルされたアセンブリは、ランタイムに読み込まれないようになりました。 これはメジャー コンポーネントとマイナー コンポーネントの組み合わせたバージョン番号に適用されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)  
 単一ファイル アセンブリおよびマルチファイル アセンブリの概要を示します。  
  
 [アセンブリ名](../../../docs/framework/app-domains/assembly-names.md)  
 アセンブリの名前付けの概要を説明します。  
  
 [方法: アセンブリの完全修飾名を特定する](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 アセンブリの完全修飾名を特定する方法を説明します。  
  
 [イントラネット アプリケーションの完全信頼での実行](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 イントラネット共有上の完全に信頼されたアセンブリに対して従来のセキュリティ ポリシーを指定する方法について説明します。  
  
 [アセンブリの場所](../../../docs/framework/app-domains/assembly-location.md)  
 アセンブリを配置する場所の概要について説明します。  
  
 [方法: シングルファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 シングルファイル アセンブリを作成する方法について説明します。  
  
 [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)  
 マルチファイル アセンブリを作成する理由について説明します。  
  
 [方法: マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 マルチファイル アセンブリを作成する方法について説明します。  
  
 [アセンブリ属性の設定](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 アセンブリの属性とその設定方法について説明します。  
  
 [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 厳密な名前でアセンブリに署名する方法と理由について説明します。方法に関するトピックが含まれています。  
  
 [アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 アセンブリに遅延署名する方法について説明します。  
  
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 アセンブリをグローバル アセンブリ キャッシュに追加する方法と理由について説明します。方法に関するトピックが含まれています。  
  
 [方法: アセンブリの内容を表示する](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 MSIL 逆アセンブラー (Ildasm.exe) を使ってアセンブリの内容を表示する方法について説明します。  
  
 [共通言語ランタイムでの型の転送](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 型の転送を使うことで、既存のアプリケーションを壊さずに異なるアセンブリに型を移動する方法について説明します。  
  
## <a name="reference"></a>関連項目  
 <xref:System.Reflection.Assembly>  
 アセンブリを表す .NET Framework クラス。  
  
## <a name="related-sections"></a>関連項目  
 [方法: アセンブリから型およびメンバーの情報を取得する](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 プログラムでアセンブリから型およびその他の情報を取得する方法について説明します。  
  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 共通言語ランタイムのアセンブリの概念的な概要について説明します。  
  
 [アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)  
 アセンブリのバインディング、および <xref:System.Reflection.AssemblyVersionAttribute> 属性と <xref:System.Reflection.AssemblyInformationalVersionAttribute> 属性の概要について説明します。  
  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 ランタイムがバインド要求を満たすために使うアセンブリを決定する方法について説明します。  
  
 [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)  
 **Reflection** クラスを使用して、アセンブリに関する情報を取得する方法を説明します。
