---
title: アセンブリ バージョンのリダイレクト
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
ms.openlocfilehash: 68169063c9cf152942ff8a7757a1b3d97886002a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034568"
---
# <a name="redirecting-assembly-versions"></a>アセンブリ バージョンのリダイレクト

コンパイル時のバインド参照のリダイレクト先として、.NET Framework アセンブリ、サードパーティ製のアセンブリ、または独自のアプリのアセンブリを指定できます。 アプリで別のバージョンのアセンブリを使用するようにリダイレクトするには、発行者ポリシーを使用する、アプリ構成ファイルを使用する、コンピューター構成ファイルを使用するなど、さまざまな方法があります。 ここでは、.NET Framework でのアセンブリ バインドの動作の仕組みと、構成方法について説明します。

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>アセンブリの統一と既定のバインド
 .NET Framework アセンブリへのバインドは、 *アセンブリの統一*というプロセスによってリダイレクトされる場合があります。 .NET Framework は、1 つのバージョンの共通言語ランタイムと、型ライブラリを構成する 24 個前後の .NET Framework アセンブリで構成されています。 これらの .NET Framework アセンブリは、ランタイムによって単一のユニットとして扱われます。 既定では、アプリを起動するとき、ランタイムによって実行されるコード内の型のすべての参照が、プロセスに読み込まれたランタイムと同じバージョン番号を持つ .NET Framework アセンブリにリダイレクトされます。 このモデルで発生するリダイレクトは、ランタイムの既定の動作となります。

 たとえば、System.XML 名前空間の型を参照するアプリケーションが、 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を使用して作成されている場合、このアプリには、ランタイム バージョン 4.5 と共に出荷された System.XML アセンブリへの静的参照が含まれます。 ここで、.NET Framework 4 と共に出荷された System.XML アセンブリを指すようにバインド参照をリダイレクトする場合は、リダイレクト情報をアプリ構成ファイルに追加します。 構成ファイルで、統一された .NET Framework アセンブリに対するバインド リダイレクトを設定すると、このアセンブリの統一が取り消されます。

 また、使用できる複数のバージョンがある場合は、サードパーティ アセンブリのアセンブリ バインドを手動でリダイレクトすることもできます。

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>発行者ポリシーを使用したアセンブリ バージョンのリダイレクト
 アセンブリの販売元は、新しいアセンブリに発行者ポリシー ファイルを含めることにより、より新しいバージョンのアセンブリにアプリをリダイレクトできます。 発行者ポリシー ファイルは、グローバル アセンブリ キャッシュに配置され、アセンブリ リダイレクトの設定が格納されます。

 アセンブリの *major*.*minor* バージョンごとに、独自の発行者ポリシー ファイルが割り当てられます。 たとえば、バージョン 2.0.2.222 から 2.0.3.000 へのリダイレクトと、バージョン 2.0.2.321 から 2.0.3.000 へのリダイレクトは、いずれもバージョン 2.0 に関連付けられているため、両方とも同じファイルに記述します。 ただし、バージョン 3.0.0.999 から 4.0.0.000 へのリダイレクトは、バージョン 3.0.999 のファイルに記述します。 .NET Framework のメジャー バージョンごとに、独自の発行者ポリシー ファイルが割り当てられます。

 アセンブリの発行者ポリシー ファイルが存在する場合、ランタイムは、アセンブリのマニフェストとアプリ構成ファイルをチェックした後で、発行者ポリシー ファイルをチェックします。 販売元は、新しいアセンブリがリダイレクト元のアセンブリとの下位互換性を維持している場合にだけ、発行者ポリシー ファイルを使用するようにします。

 「 [発行者ポリシーの省略](#bypass_PP)」で説明するように、アプリ構成ファイルで設定を指定することによって、アプリの発行者ポリシーを省略することができます。

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>アプリ レベルでのアセンブリ バージョンのリダイレクト
 アプリ構成ファイルを通じてアプリのバインド動作を変更するには、いくつかの手法があります。手動でのファイルの編集、自動バインド リダイレクトの利用、発行者ポリシーの省略によるバインド動作の指定を行うことができます。

### <a name="manually-editing-the-app-config-file"></a>手動でのアプリ構成ファイルの編集
 手動でアプリ構成ファイルを編集して、アセンブリの問題を解決できます。 たとえば、販売元が、アプリで使用しているアセンブリの新しいバージョンをリリースしたが、下位互換性を保証していないために、発行者ポリシーを提供しない場合でも、次のように、アプリ構成ファイルにアセンブリ バインド情報を記述することによって、アプリで新しいバージョンのアセンブリを使用するように指示できます。

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>自動バインド リダイレクトの利用

作成するとき、デスクトップ アプリを Visual Studio を対象とする、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]または以降のバージョンが、アプリは、自動バインド リダイレクトを使用します。 これは、2 つのコンポーネントが同じ厳密な名前付きアセンブリの異なるバージョンを参照する場合、ランタイムは出力するアプリ構成ファイル (app.config) に新しいバージョンのアセンブリへのバインド リダイレクトを自動的に追加することを意味します。 このリダイレクトは、別の方法で発生する可能性があるアセンブリの統一をオーバーライドします。 ソース app.config ファイルは変更されません。 たとえば、アプリがアウトオブバンド .NET Framework コンポーネントを直接参照する場合に、同じコンポーネントの旧バージョンを対象とするサードパーティのライブラリを使用しているとします。 このアプリをコンパイルすると、出力されるアプリ構成ファイルは、新しいバージョンのコンポーネントへのバインド リダイレクトを含むように変更されます。 Web アプリを作成すると、バインドの競合に関するビルドの警告が表示され、ソース Web 構成ファイルに必要なバインド リダイレクトを追加するためオプションが示されます。

コンパイル時にソース app.config ファイルに手動でバインド リダイレクトを追加する場合、Visual Studio は、追加したバインド リダイレクトに基づいてアセンブリの統一しようとします。 たとえば、アセンブリの次のバインド リダイレクトを挿入するとします。

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

アプリ内の別のプロジェクトが同じアセンブリのバージョン 1.0.0.0 を参照する場合、自動バインド リダイレクトは、アプリがこのアセンブリのバージョン 2.0.0.0 で統一されるように、出力 app.config ファイルに次のエントリを追加します。

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

アプリの対象が .NET Framework の旧バージョンの場合は、自動バインド リダイレクトを有効にできます 任意のアセンブリの app.config ファイルにバインド リダイレクト情報を提供することで、またはバインド リダイレクト機能を無効にすることで、この既定の動作をオーバーライドできます この機能を有効または無効にする方法については[、[自動バインディング リダイレクトを有効/無効にする方法](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)」を参照してください自動バインディング リダイレクトを有効/無効にする](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)」をご覧ください。

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>発行者ポリシーの省略
 アプリの構成ファイルの発行者ポリシーを必要に応じてオーバーライドできます。 たとえば、下位互換性を維持しているとされる新しいアセンブリ バージョンでも、アプリを破壊する可能性があります。 発行者ポリシーをバイパスする場合は、追加、 [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)要素を[ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)アプリ構成ファイル、および、セット内の要素**適用**属性を**ありません**、前が優先されます**はい**設定します。

 `<publisherPolicy apply="no" />`

 発行者ポリシーを省略することにより、アプリの実行を続行できますが、必ず、問題点をアセンブリの販売元に報告してください。 アセンブリに発行者ポリシー ファイルを提供した場合、販売元はそのアセンブリが下位互換性を維持していること、およびクライアントが可能な限り新バージョンを使用できることを確認する必要があります。

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>コンピューター レベルでのアセンブリ バージョンのリダイレクト
 コンピューター管理者が 1 台のコンピューター上のすべてのアプリで特定のアセンブリ バージョンを使用する場合も、まれにあります。 たとえば、セキュリティ ホールを修復するために、すべてのアプリで特定のアセンブリ バージョンを使用する場合があります。 コンピューターの構成ファイル内でアセンブリをリダイレクトした場合は、そのコンピューターで旧バージョンを使用しているすべてのアプリが新バージョンを使用するようになります。 コンピューター構成ファイルは、アプリ構成ファイルおよび発行者ポリシー ファイルよりもオーバーライドされます。 このファイルは、%*runtime install path*%\Config ディレクトリに含まれています。 通常、.NET Framework は %drive%\Windows\Microsoft.NET\Framework ディレクトリにインストールされます。

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>構成ファイル内でのアセンブリ バインドの指定
 アプリ構成ファイル、コンピューター構成ファイル、発行者ポリシー ファイルのいずれの場合も、同じ XML 形式を使用してバインド リダイレクトを指定できます。 使用して、別の 1 つのアセンブリ バージョンをリダイレクトする、 [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)要素。 **oldVersion** 属性では、1 つのアセンブリ バージョンまたはバージョンの範囲を指定できます。 `newVersion` 属性では、1 つのバージョンを指定する必要があります。  たとえば、 `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` は、アセンブリ バージョン 1.1.0.0 ～ 1.2.0.0 の代わりにバージョン 2.0.0.0 を使用するようにランタイムに指示します。

 次のコード例は、さまざまなバインディング リダイレクトのシナリオを示しています。 この例では、 `myAssembly`のバージョンの範囲に対するリダイレクトと、 `mySecondAssembly`の単一のバインド リダイレクトを指定します。 この例では、発行者ポリシー ファイルによって `myThirdAssembly`のバインド リダイレクトがオーバーライドされないことも指定しています。

 アセンブリをバインドするには、文字列を指定する必要があります"urn: スキーマ-microsoft-com:asm.v1"で、 **xmlns**属性、 [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)タグ。

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
  <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>特定のバージョンへのアセンブリ バインドの制限
 使用することができます、 **appliesTo**属性を[ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)アセンブリ バインディング参照を .NET の特定のバージョンをリダイレクトするアプリ構成ファイル内の要素フレームワーク。 このオプションの属性では、.NET Framework バージョン番号を使用して、適用するバージョンを指定します。 **appliesTo** 属性が指定されていない場合、[\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 要素は、.NET Framework のすべてのバージョンに適用されます。

 たとえば、.NET Framework 3.5 アセンブリのアセンブリ バインドをリダイレクトするには、アプリ構成ファイルに次の XML コードを追加します。

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 バージョンの順序でリダイレクト情報を入力する必要があります。 たとえば、.NET Framework 3.5 アセンブリのアセンブリ バインド リダイレクト情報を入力し、次に .NET Framework 4.5 アセンブリの情報を入力します。 最後に、 **appliesTo** 属性を使用せず、すべてのバージョンの .NET Framework に適用される .NET Framework アセンブリ リダイレクトのアセンブリ バインディング リダイレクト情報を入力します。 リダイレクトで競合が発生した場合は、構成ファイル内で最初に一致したリダイレクト ステートメントが使用されます。

 たとえば、ある参照を .NET Framework 3.5 のアセンブリにリダイレクトし、別の参照を .NET Framework 4 のアセンブリにリダイレクトするには、次の擬似コードに示すパターンを使用します。

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>関連項目

- [方法: 自動バインディング リダイレクトを有効/無効にする](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect > 要素](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [アセンブリ バインディング リダイレクトのセキュリティ アクセス許可](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)
- [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [アプリの構成](../../../docs/framework/configure-apps/index.md)
- [ランタイム設定スキーマ](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)
- [方法: 発行者ポリシーを作成します。](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
