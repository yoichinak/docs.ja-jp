---
title: .NET アプリのリソース
description: .NET アプリのリソースについて理解します。 リソースとは、アプリと共に論理的に配置される、実行不可能な任意のデータです。
ms.date: 07/25/2018
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- deploying applications [.NET Core], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
ms.openlocfilehash: 105325170389917bfb2022314791aa1ed5923db3
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865165"
---
# <a name="resources-in-net-apps"></a>.NET アプリのリソース

ほとんどの製品レベルのアプリでは、リソースを使用する必要があります。 リソースとは、アプリと共に論理的に配置される、実行不可能な任意のデータです。 リソースは、アプリ内でエラー メッセージとして表示されたり、ユーザー インターフェイスの一部として表示されたりします。 リソースには、文字列、画像、永続化されたオブジェクトなど、多数の形式のデータを含めることができます。 (永続化されたオブジェクトをリソース ファイルに書き込むには、そのオブジェクトをシリアル化できる必要があります。) データをリソース ファイルに格納しておけば、アプリ全体を再コンパイルすることなくデータを変更できます。 また、データの格納場所が 1 つになり、複数の場所に格納されているハードコーディングされたデータを利用する必要がなくなります。

.NET Framework および .NET Core では、リソースの作成とローカライズが包括的にサポートされます。 さらに、.NET では、ローカライズされたリソースのパッケージ化および配置のためのシンプルなモデルがサポートされています。

ASP.NET のリソースについては、「[ASP.NET Web ページのリソースの概要](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100))」を参照してください。

## <a name="create-and-localize-resources"></a>リソースを作成してローカライズする

ローカライズされていないアプリでは、リソース ファイルをアプリ データ、特にソース コード内の複数の場所にハードコーディングされる可能性がある文字列のリポジトリとして使用できます。 ほとんどの場合、リソースはテキスト (.txt) ファイルまたは XML (.resx) ファイルとして作成し、[Resgen.exe (リソース ファイル ジェネレーター)](../tools/resgen-exe-resource-file-generator.md) を使用して .resources バイナリ ファイルにコンパイルします。 その後、これらのファイルを、言語コンパイラによってアプリの実行可能ファイルに埋め込むことができます。 リソースの作成の詳細については、[リソース ファイルの作成](creating-resource-files-for-desktop-apps.md)に関する記事を参照してください。

アプリのリソースを特定のカルチャに合わせてローカライズすることもできます。 これにより、アプリのローカライズ (翻訳) バージョンを構築できます。 ローカライズされたリソースを使用するアプリを開発する場合、ニュートラル カルチャまたはフォールバック カルチャとして使用するカルチャを指定します。適切なリソースを利用できない場合には、そのカルチャのリソースが使用されます。 一般に、ニュートラル カルチャのリソースはアプリの実行可能ファイルに格納されます。 個々のローカライズされたカルチャ用のその他のリソースは、スタンドアロンのサテライト アセンブリに格納されます。 詳細については、[サテライト アセンブリの作成](creating-satellite-assemblies-for-desktop-apps.md)に関する記事を参照してください。

## <a name="package-and-deploy-resources"></a>リソースをパッケージ化して配置する

ローカライズされたアプリ リソースは[サテライト アセンブリ](packaging-and-deploying-resources-in-desktop-apps.md)に配置します。 サテライト アセンブリには 1 つのカルチャのリソースが含まれます。アプリ コードは含まれません。 サテライト アセンブリの配置モデルでは、1 つの既定アセンブリ (一般的にはメイン アセンブリ) と、アプリがサポートするカルチャごとに 1 つのサテライト アセンブリを使用するアプリを作成します。 サテライト アセンブリはメイン アセンブリには含まれないため、アプリのメイン アセンブリを交換しなくても、特定のカルチャに対応するリソースのみを簡単に置換または更新できます。

どのリソースをアプリの既定のリソース アセンブリに含めるかは、慎重に決定してください。 これはメイン アセンブリの一部に含まれるため、変更するためにはメイン アセンブリを置き換える必要が生じます。 既定のリソースを提供しないと、[リソース フォールバック プロセス](packaging-and-deploying-resources-in-desktop-apps.md)によって既定のリソースが検索されるときに例外が発生します。 アプリが適切にデザインされていれば、リソースの使用によって例外が発生することはありません。

詳細については、[リソースのパッケージ化と配置](packaging-and-deploying-resources-in-desktop-apps.md)に関する記事を参照してください。

## <a name="retrieve-resources"></a>リソースを取得する

アプリでは、実行時に、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> プロパティで指定されるカルチャに基づいて、適切なローカライズ バージョンのリソースがスレッド単位で読み込まれます。 このプロパティ値の派生は次のように行われます。

- ローカライズされたカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトを <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> プロパティに直接割り当てます。

- カルチャが明示的に割り当てられていない場合は、<xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> プロパティから既定のスレッド UI カルチャを取得します。

- 既定のスレッド UI カルチャが明示的に割り当てられていない場合は、ローカル コンピューター上の現在のユーザーのカルチャを取得します。 Windows 上で実行されている .NET 実装では、Windows の [`GetUserDefaultUILanguage`](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) 関数を呼び出すことによってそれが行われます。

現在の UI カルチャを設定する方法の詳細については、<xref:System.Globalization.CultureInfo> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> のリファレンス ページを参照してください。

これで、<xref:System.Resources.ResourceManager?displayProperty=nameWithType> クラスを使用して、現在の UI カルチャまたは特定のカルチャのリソースを取得できます。 <xref:System.Resources.ResourceManager> クラスは、リソースを取得する場合に最もよく使用されますが、<xref:System.Resources?displayProperty=nameWithType> 名前空間には、リソースの取得に使用できるその他の型も含まれています。 次のようなものがあります。

- <xref:System.Resources.ResourceReader> クラス。アセンブリに埋め込まれているリソースまたはスタンドアロンの .resources バイナリ ファイルに格納されているリソースを列挙できます。 これは、実行時に使用可能なリソースの正確な名前がわからない場合に役立ちます。

- <xref:System.Resources.ResXResourceReader> クラス。XML (.resx) ファイルからリソースを取得できます。

- <xref:System.Resources.ResourceSet> クラス。フォールバック規則に従わずに特定のカルチャのリソースを取得できます。 リソースは、アセンブリ、またはスタンドアロンの .resources バイナリ ファイルに格納できます。 また、<xref:System.Resources.IResourceReader> の実装も開発できます。この実装によって、<xref:System.Resources.ResourceSet> クラスを使用して他のソースからリソースを取得できるようになります。

- <xref:System.Resources.ResXResourceSet> クラス。XML リソース ファイル内のすべての項目を取得してメモリに格納できます。

## <a name="see-also"></a>関連項目

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [リソース ファイルの作成](creating-resource-files-for-desktop-apps.md)
- [リソースのパッケージ化と配置](packaging-and-deploying-resources-in-desktop-apps.md)
- [サテライト アセンブリの作成](creating-satellite-assemblies-for-desktop-apps.md)
- [リソースの取得](retrieving-resources-in-desktop-apps.md)
