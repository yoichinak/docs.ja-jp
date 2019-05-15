---
title: マルチファイル アセンブリ
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e00ec239fbe5d5963edd3a7656961556792c6324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593555"
---
# <a name="multifile-assemblies"></a>マルチファイル アセンブリ

コマンド ライン コンパイラまたは Visual C++ で Visual Studio を使って、マルチファイル アセンブリを作成できます。 アセンブリ内の 1 つのファイルには、アセンブリ マニフェストが含まれている必要があります。 アプリケーションを起動するアセンブリには、Main メソッドや WinMain メソッドなどのエントリ ポイントも含まれている必要があります。

たとえば、2 つのコード モジュール Client.cs と Stringer.cs を含むアプリケーションがあるものとします。 Stringer.cs は、Client.cs 内のコードによって参照される `myStringer` 名前空間を作成します。 Client.cs には、アプリケーションのエントリ ポイントである `Main` メソッドが含まれます。 この例では、2 つのコード モジュールをコンパイルし、さらにアプリケーションを起動するアセンブリ マニフェストを含む 3 番目のファイルを作成します。 アセンブリ マニフェストは、`Client` モジュールと `Stringer` モジュールの両方を参照します。

> [!NOTE]
> アセンブリに複数のコード モジュールがある場合でも、マルチファイル アセンブリが持つことのできるエントリ ポイントは 1 つだけです。

マルチファイル アセンブリを作成するのにはいくつかの理由があります。

- 異なる言語で記述されたモジュールを結合するため。 これは、マルチファイル アセンブリを作成する最も一般的な理由です。

- 使用頻度の低い型を、必要なときにだけダウンロードされるモジュールに入れることにより、アプリケーションのダウンロードを最適化するため。

    > [!NOTE]
    > Microsoft Internet Explorer で `<object>` タグを使ってダウンロードされるアプリケーションを作成する場合は、マルチファイル アセンブリを作成することが重要です。 このシナリオでは、コード モジュールとは別に、アセンブリ マニフェストだけを含むファイルを作成します。 Internet Explorer は、最初にアセンブリ マニフェストをダウンロードした後、ワーカー スレッドを作成して、追加のモジュールまたは必要なアセンブリをダウンロードします。 アセンブリ マニフェストが含まれるファイルがダウンロードしている間、Internet Explorer はユーザー入力に応答できません。 アセンブリ マニフェストを含むファイルが小さいほど、Internet Explorer が応答しない時間が短くなります。

- 複数の開発者が記述したコード モジュールを結合するため。 開発者ごとに各コード モジュールをアセンブリにコンパイルすることもできますが、そうすると、すべてのモジュールがマルチファイル アセンブリに収められている場合であれば公開されない一部の型が強制的に公開されることがあります。

アセンブリを作成した後は、アセンブリ マニフェスト (以降アセンブリ) を含むファイルに署名したり、ファイル (およびアセンブリ) に厳密な名前を付けて、グローバル アセンブリ キャッシュに配置したりすることができます。

## <a name="see-also"></a>関連項目

- [方法: マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)