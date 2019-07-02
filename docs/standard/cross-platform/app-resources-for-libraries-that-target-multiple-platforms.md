---
title: 複数のプラットフォームを対象とするライブラリのアプリケーション リソース
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e846f45b55ac09d6ce6af4f3223c3bdba1dc83ba
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506014"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>複数のプラットフォームを対象とするライブラリのアプリケーション リソース
.NET Framework を使用して[ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)プロジェクトの種類が、クラス ライブラリのリソースを複数のプラットフォームからアクセスできることを確認します。 このプロジェクトの種類では、Visual Studio 2012 で使用できる、.NET Framework クラス ライブラリの移植可能なサブセットを対象とします。 ポータブル クラス ライブラリを使用して、デスクトップ アプリ、Silverlight アプリ、Windows Phone のアプリから、ライブラリにアクセスできることにより、および[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 ポータブル クラス ライブラリ プロジェクト内の型の非常に限定されたサブセットのみを使用する、<xref:System.Resources>には、アプリケーションで使用できる名前空間には、使用することは、<xref:System.Resources.ResourceManager>クラス リソースを取得します。 ただし、Visual Studio を使用してアプリケーションを作成する場合は、<xref:System.Resources.ResourceManager> クラス ライブラリを使用するのではなく、Visual Studio によって作成された厳密に型指定されたラッパーを使用する必要があります。

 Visual Studio では、厳密に型指定されたラッパーを作成、設定、メイン リソース ファイルの**アクセス修飾子**を Visual Studio リソース デザイナーで**パブリック**します。 これにより、厳密に型指定された ResourceManager ラッパーを含む [resourceFileName].designer.cs または [resourceFileName].designer.vb ファイルが作成されます。 厳密に型指定されたリソース ラッパーの使用方法の詳細については、"厳密に型指定されたリソース クラスの生成」セクションを参照してください、 [Resgen.exe (リソース ファイル ジェネレーター)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)トピック。

## <a name="resource-manager-in-the-portable-class-library"></a>ポータブル クラス ライブラリにリソース マネージャー
 ポータブル クラス ライブラリ プロジェクトでリソースへのすべてのアクセスは、によって処理されます、<xref:System.Resources.ResourceManager>クラス。 ため、型、<xref:System.Resources>名前空間など<xref:System.Resources.ResourceReader>と<xref:System.Resources.ResourceSet>はポータブル クラス ライブラリ プロジェクトからはアクセスできない、使用できませんのリソースにアクセスします。

 ポータブル クラス ライブラリ プロジェクトには、4 つが含まれています。<xref:System.Resources.ResourceManager>メンバーは、次の表に一覧表示します。 これらのコンストラクターおよびメソッドを使用すると、<xref:System.Resources.ResourceManager> オブジェクトをインスタンス化して文字列リソースを取得できます。

|`ResourceManager` のメンバー|説明|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|<xref:System.Resources.ResourceManager> インスタンスを作成し、指定されたアセンブリ内にある、名前の指定されたリソース ファイルにアクセスします。|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|指定された型に対応する <xref:System.Resources.ResourceManager> インスタンスを作成します。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|現在のカルチャに対する、名前の指定されたリソースを取得します。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|指定されたカルチャに属する、名前の指定されたリソースを取得します。|

 その他の除外<xref:System.Resources.ResourceManager>オブジェクト、文字列以外のデータ、およびイメージをシリアル化するポータブル クラス ライブラリの手段のメンバーは、リソース ファイルから取得できません。 ポータブル クラス ライブラリからリソースを使用するには、文字列の形式でオブジェクトのすべてのデータを格納する必要があります。 たとえば、数値を文字列に変換してリソース ファイルに格納し、これらを取得して、数値データ型の `Parse` メソッドまたは `TryParse` メソッドを使用して数値に戻すことができます。 イメージや他のバイナリ データを文字列形式に変換するには <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> メソッドを呼び出し、バイト配列に戻すには <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> メソッドを呼び出します。

## <a name="the-portable-class-library-and-windows-store-apps"></a>ポータブル クラス ライブラリと Windows ストア アプリ
 ポータブル クラス ライブラリ プロジェクトでは、.resx ファイルには、.resources ファイルにコンパイルされ、メイン アセンブリまたはサテライト アセンブリをコンパイル時に埋め込まれたリソースを格納します。 一方、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーションではリソースを .resw ファイルに格納する必要があります。このファイルはその後、単一のパッケージ リソース インデックス (PRI) ファイルにコンパイルされます。 ただし、互換性のないファイルの形式に関係なく、ポータブル クラス ライブラリは動作、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ。

 クラス ライブラリを [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーションで使用するには、Windows ストア アプリケーション プロジェクトでその参照を追加します。 Visual Studio は透過的に .resw ファイルに、アセンブリからリソースを抽出し、Windows ランタイムがリソースを抽出 PRI ファイルの生成に使用します。 実行時に、Windows ランタイムで、ポータブル クラス ライブラリのコードを実行しますが、ポータブル クラス ライブラリのリソースは PRI ファイルから取得します。

 ポータブル クラス ライブラリ プロジェクトには、ローカライズされたリソースが含まれている場合は、デスクトップ アプリでのライブラリと同様に展開するため、ハブ アンド スポーク モデルを使用します。 メイン リソース ファイルおよびローカライズされたリソース ファイルを [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーションで使用するには、参照をメイン アセンブリに追加します。 コンパイル時に、Visual Studio はメイン リソース ファイルとローカライズされているリソース ファイルからリソースを個別の .resw ファイルに抽出します。 実行時に、Windows ランタイムにアクセスする単一の PRI ファイルに .resw ファイルをコンパイルします。

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>例:ローカライズのポータブル クラス ライブラリ
 次のシンプルでローカライズされていないポータブル クラス ライブラリの例は、列の名前を格納し、表形式のデータ用に予約する文字数を決定する、リソースを使用します。 この例では LibResources.resx という名前のファイルを使用して、次の表に示す文字列リソースを格納します。

|リソース名|リソースの値|
|-------------------|--------------------|
|Born|Birthdate|
|BornLength|12|
|Hired|Hire Date|
|HiredLength|12|
|ID|ID|
|ID.Length|12|
|Name|Name|
|NameLength|25|
|Title|従業員データベース|

 次のコード定義を`UILibrary`という名前のリソース マネージャーのラッパーを使用するクラス`resources`Visual Studio によって生成されたときに、**アクセス修飾子**にファイルが変更**パブリック**. UILibrary クラスは必要に応じて文字列データを解析します。 . このクラスは `MyCompany.Employees` 名前空間にあることに注意してください。

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 次のコードは、`UILibrary` クラスとそのリソースをコンソールモード アプリケーションからアクセスする方法を示します。 コンソール アプリのプロジェクトに追加するのには UILibrary.dll への参照が必要です。

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 次のコードは、`UILibrary` クラスとそのリソースを [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーションからアクセスする方法を示します。 Windows ストア アプリのプロジェクトに追加するのには UILibrary.dll への参照が必要です。

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>例:ローカライズされたポータブル クラス ライブラリ
 次のローカライズされたポータブル クラス ライブラリの例には、フランス語 (フランス) と英語 (米国) カルチャのリソースが含まれます。 英語 (米国) カルチャは、アプリの既定のカルチャです。テーブルにそのリソースが示すように、[前のセクション](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc)します。 フランス語 (フランス) のカルチャのリソース ファイルは LibResources.fr-FR.resx という名前で、以下の表に示す文字列リソースで構成されています。 `UILibrary` クラスのソース コードは前のセクションに示すものと同じです。

|リソース名|リソースの値|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|ID|ID|
|Name|Nom|
|Title|Base de données des employés|

 次のコードは、`UILibrary` クラスとそのリソースをコンソールモード アプリケーションからアクセスする方法を示します。 コンソール アプリのプロジェクトに追加するのには UILibrary.dll への参照が必要です。

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 次のコードは、`UILibrary` クラスとそのリソースを [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーションからアクセスする方法を示します。 Windows ストア アプリのプロジェクトに追加するのには UILibrary.dll への参照が必要です。 静的な `ApplicationLanguages.PrimaryLanguageOverride` プロパティを使用してアプリケーションの優先言語をフランス語に設定します。

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Resources.ResourceManager>
- [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)
- [リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
