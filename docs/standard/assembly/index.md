---
title: .NET のアセンブリ
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
---
# <a name="assemblies-in-net"></a>.NET のアセンブリ

アセンブリは、.NET ベースのアプリケーションの配置、バージョン管理、再利用、アクティベーション スコープ、およびセキュリティ権限の基本単位です。 アセンブリは、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルの形を取る、.NET アプリケーションの構成要素です。 それらは、型の実装に関して必要な情報を共通言語ランタイムに提供します。 アセンブリは、機能的な論理的な単位を形成し、連携して動作するように構築された、型とリソースのコレクションと考えることができます。

.NET Core と .NET Framework では、1 つまたは複数のソース コード ファイルからアセンブリをビルドできます。 .NET Framework では、アセンブリに 1 つまたは複数のモジュールを含めることができます。 これを使うと、複数の個別の開発者が別々のソース コード ファイルやモジュールで作業し、それらを組み合わせて 1 つのアセンブリを作成することで、より大規模なプロジェクトの計画が可能になります。 モジュールについて詳しくは、「[方法:マルチファイル アセンブリをビルドする](../../framework/app-domains/how-to-build-a-multifile-assembly.md)」をご覧ください。

アセンブリには、次の特徴があります。

- アセンブリは、.exe または .dll ファイルとして実装されます。

- .NET Framework をターゲットにするライブラリの場合、アセンブリを[グローバル アセンブリ キャッシュ](../../framework/app-domains/gac.md)に配置することで、それをアプリケーション間で共有することができます。 グローバル アセンブリ キャッシュに含める前に、アセンブリに厳密な名前を付ける必要があります。 詳細については、「[厳密な名前付きアセンブリ](../../framework/app-domains/strong-named-assemblies.md)」を参照してください。

- アセンブリは、必要な場合にのみメモリに読み込まれます。 使用されない場合、読み込まれることはありません。 これは、アセンブリを使用すると、大規模なプロジェクト内のリソースを効率的に管理できることを意味します。

- リフレクションを使用して、アセンブリに関する情報をプログラムによって取得できます。 詳細については、「[リフレクション (C#)](../../csharp/programming-guide/concepts/reflection.md)」または「[リフレクション (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md)」をご覧ください。

- アセンブリの読み込みは、<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> メソッドを呼び出してそれを検査するためにのみ実行できます。

## <a name="assembly-manifest"></a>アセンブリ マニフェスト

すべてのアセンブリの中にあるのが "*アセンブリ マニフェスト*" です。 目次と同じように、アセンブリ マニフェストには次の項目が含まれます。

- アセンブリの ID (名前とバージョン)。

- アセンブリを構成するその他すべてのファイルについて記述するファイル テーブル (自分で作成したその他のアセンブリで .exe や .dll ファイルが依存しているもの、またはビットマップや Readme ファイルなど)。

- "*アセンブリ参照リスト*"。これは、すべての外部依存関係の一覧です。アプリケーションが必要とする .dll ファイルやその他のファイルであり、他のユーザーが作成したものを含む場合もあります。 アセンブリ参照には、グローバルおよびプライベートの両方のオブジェクトへの参照が含まれます。 グローバル オブジェクトは、その他のすべてのアプリケーションで利用できます。 .NET Core では、それらは特定の .NET Core ランタイムと組み合わされます。 .NET Framework では、それらはグローバル アセンブリ キャッシュ内にあります。 <xref:System.IO?displayProperty=nameWithType> 名前空間は、グローバル アセンブリ キャッシュ内のアセンブリの例です。 プライベート オブジェクトは、アプリケーションがインストールされているディレクトリと同じレベルまたはその下のディレクトリ内に存在する必要があります。

アセンブリにはコンテンツ、バージョン管理、および依存関係に関する情報が含まれているため、それらを使用するアプリケーションは、Windows のレジストリ値に依存しなくても正常に機能することができます。 アセンブリは、.dll の競合を減らし、アプリケーションの信頼性を高め、配置を容易にします。 多くの場合、.NET ベースのアプリケーションは、ターゲット コンピューターにそのファイルをコピーするだけでインストールすることができます。 詳細については、「[アセンブリ マニフェスト](../../framework/app-domains/assembly-manifest.md)」を参照してください。

## <a name="adding-a-reference-to-an-assembly"></a>アセンブリへの参照の追加

アセンブリを使用するには、アセンブリへの参照を追加する必要があります。 次に、C# の [using ディレクティブ](../../csharp/language-reference/keywords/using-directive.md)、または Visual Basic の [Imports ステートメント](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を使って、使用する項目の名前空間を選択できます。 アセンブリが参照されてインポートされた後は、その名前空間のアクセス可能なすべての型、プロパティ、メソッド、およびのその他のメンバーを、そのコードがご自分のソース ファイルの一部であるかのようにアプリケーションで使用することができます。

> [!NOTE]
> .NET クラス ライブラリのほとんどのアセンブリは自動的に参照されます。 ただし、場合によっては、システム アセンブリが自動的に参照されない場合があります。 .NET Core では、アセンブリを含む NuGet パッケージへの参照を追加するには、Visual Studio の NuGet パッケージ マネージャーを使用するか、アセンブリの [<PackageReference>](../../core/tools/dependencies.md#the-new-packagereference-element) 要素を *.csproj または *.vbproj プロジェクトに追加します。 .NET Framework では、アセンブリへの参照を追加するには、Visual Studio の **[参照の追加]** ダイアログを使用するか、[C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) または [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) コンパイラに向けてコマンド ライン オプション `-reference` を使用します。

C# では、1 つのアプリケーションで同じアセンブリの 2 つのバージョンを使用することもできます。 詳細については、「[extern エイリアス](../../csharp/language-reference/keywords/extern-alias.md)」を参照してください。

## <a name="creating-an-assembly"></a>アセンブリの作成

アプリケーションをコンパイルするには、それを Visual Studio でビルドするか、.NET Core コマンド ライン インターフェイス (CLI) ツールを使ってコマンド ラインからそれをビルドするか、またはコマンド ライン コンパイラを使って .NET Framework アセンブリをビルドします。 .NET CLI ツールを使ったアセンブリのビルドについて詳しくは、「[.NET Core コマンドライン インターフェイス (CLI) ツール](../../core/tools/index.md)」をご覧ください。 コマンド ライン コンパイラを使ったアセンブリのビルドについては、「[csc.exe を使用したコマンド ラインからのビルド](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」(C#)、および[コマンド ラインからのビルド](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Visual Basic) に関する記事をご覧ください。

> [!NOTE]
> Visual Studio でアセンブリをビルドするには、**[ビルド]** メニューの **[ビルド]** を選択します。

## <a name="see-also"></a>関連項目

- [.NET アセンブリ ファイルの形式](file-format.md)
- [共通言語ランタイムのアセンブリ](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [フレンド アセンブリ](friend-assemblies.md)
- [方法: アセンブリを読み込み、アンロードする (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [方法: アセンブリを読み込み、アンロードする (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [方法: .NET Core でアセンブリのアンローダビリティを使用およびデバッグする](unloadability-howto.md)
- [方法: ファイルがアセンブリであるかどうかを確認する (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [方法: ファイルがアセンブリであるかどうかを確認する (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
