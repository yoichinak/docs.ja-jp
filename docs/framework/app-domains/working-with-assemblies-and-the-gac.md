---
title: アセンブリとグローバル アセンブリ キャッシュの使用
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62760cb9fe5832ee018ebdebf6275ea61691c738
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927801"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>アセンブリとグローバル アセンブリ キャッシュの使用
あるアセンブリを複数のアプリケーションで共有する場合は、そのアセンブリをグローバル アセンブリ キャッシュ内にインストールできます。 共通言語ランタイムをインストールしている各コンピューターは、このコードをコンピューター全体で使用できます。 グローバル アセンブリ キャッシュは、そのコンピューター上の複数のアプリケーションで共有するように指定されたアセンブリを格納します。 グローバル アセンブリ キャッシュ内にインストールされるアセンブリは、厳密な名前を持つ必要があります。  
  
> [!NOTE]
> グローバル アセンブリ キャッシュ内に配置されるアセンブリは、アセンブリ名とファイル名の拡張子を除く部分が一致している必要があります。 たとえば、アセンブリ名が myAssembly のアセンブリの場合、ファイル名は myAssembly.exe または myAssembly.dll である必要があります。  
  
 アセンブリの共有が必要な場合にだけ、アセンブリをグローバル アセンブリ キャッシュにインストールします。 一般的には、明らかにアセンブリを共有する必要がある場合を除いて、アセンブリの依存関係はプライベートにし、アセンブリはアプリケーション ディレクトリに配置します。 また、COM 相互運用 (機能) またはアンマネージ コードからアセンブリにアクセスできるようにするために、アセンブリをグローバル アセンブリ キャッシュにインストールする必要はありません。  
  
 アセンブリをグローバル アセンブリ キャッシュにインストールする理由は、いくつか考えられます。  
  
- 共有の場所。  
  
     複数のアプリケーションで使用するアセンブリは、グローバル アセンブリ キャッシュに配置できます。 たとえば、すべてのアプリケーションがグローバル アセンブリ キャッシュ内の 1 つのアセンブリを使用する場合は、アセンブリへの参照をリダイレクトするバージョン ポリシー ステートメントを Machine.config ファイルに追加できます。  
  
- ファイル セキュリティ。  
  
     通常、管理者は、書き込みおよび実行アクセスを制御するアクセス制御リスト (ACL: Access Control List) を使用して systemroot ディレクトリを保護します。 グローバル アセンブリ キャッシュは、systemroot ディレクトリにインストールされるため、このディレクトリの ACL を継承します。 グローバル アセンブリ キャッシュからファイルを削除する場合は、管理者権限を持つユーザーに対してだけ許可することをお勧めします。  
  
- side-by-side でのバージョン管理。  
  
     名前は同じでもバージョン情報が異なるアセンブリの複数のコピーを、グローバル アセンブリ キャッシュ内で管理できます。  
  
- 追加の検索場所。  
  
     共通言語ランタイムは、構成ファイル内のコードベース情報をプローブまたは使用する前に、グローバル アセンブリ キャッシュ内にアセンブリ要求と一致するアセンブリがあるかどうかをチェックします。  
  
 アセンブリのグローバル アセンブリ キャッシュへのインストールを明示的に避けたい場合もあります。 アプリケーションを構成するアセンブリの 1 つをグローバル アセンブリ キャッシュに配置した場合は、アプリケーション ディレクトリをコピーする XCOPY を使用してアプリケーションをレプリケートしたりインストールしたりすることはできなくなります。 この場合は、グローバル アセンブリ キャッシュ内のアセンブリも移動する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: アセンブリをグローバル アセンブリ キャッシュにインストールする](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 アセンブリをグローバル アセンブリ キャッシュにインストールする方法について説明します。  
  
 [方法: グローバル アセンブリ キャッシュの内容を表示する](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 [グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュの内容を表示する方法について説明します。  
  
 [方法: グローバル アセンブリ キャッシュからアセンブリを削除する](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュからアセンブリを削除する方法について説明します。  
  
 [サービス コンポーネントとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 サービス コンポーネント (マネージド COM+ コンポーネント) をグローバル アセンブリ キャッシュに配置する必要がある理由について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)  
 アセンブリの作成の概要を説明します。  
  
 [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)  
 グローバル アセンブリ キャッシュについて説明します。  
  
 [方法: アセンブリの内容を表示する](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリ内の MSIL (Microsoft Intermediate Language) 情報を表示する方法について説明します。  
  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 共通言語ランタイムが、アプリケーションを構成するアセンブリを検出して読み込む方法について説明します。  
  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 マネージド アプリケーションを構成するブロックであるアセンブリについて説明します。
