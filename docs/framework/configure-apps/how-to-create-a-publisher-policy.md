---
title: '方法: 発行者ポリシーを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646054"
---
# <a name="how-to-create-a-publisher-policy"></a>方法: 発行者ポリシーを作成する

アセンブリのベンダーは、アップグレードされたアセンブリに発行者ポリシー ファイルを含めることによって、アプリケーションが新しいバージョンのアセンブリを使用する必要があることを示すことができます。 発行者ポリシー ファイルは、アセンブリ リダイレクトとコード ベースの設定を指定し、アプリケーション構成ファイルと同じ形式を使用します。 発行者ポリシー ファイルは、アセンブリにコンパイルされ、グローバル アセンブリ キャッシュに格納されます。

発行者ポリシーの作成には、次の 3 つの手順があります。

1. 発行者ポリシー ファイルを作成します。

2. 発行者ポリシー アセンブリを作成します。

3. 発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。

発行者ポリシーのスキーマについては、「アセンブリ[バージョンのリダイレクト」を参照してください](redirect-assembly-versions.md)。 次の例は、あるバージョンののを別の`myAssembly`バージョンにリダイレクトする発行者ポリシー ファイルを示しています。

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

コード ベースを指定する方法については、「[アセンブリの場所を指定する](specify-assembly-location.md)」を参照してください。

## <a name="creating-the-publisher-policy-assembly"></a>発行者ポリシー アセンブリの作成

アセンブリ[リンカー (Al.exe) を](../tools/al-exe-assembly-linker.md)使用して、発行者ポリシー アセンブリを作成します。

#### <a name="to-create-a-publisher-policy-assembly"></a>発行者ポリシー アセンブリを作成するには

コマンド プロンプトに、次のコマンドを入力します。

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

このコマンドの説明:

- 引数`publisherPolicyFile`は、発行者ポリシー ファイルの名前です。

- 引数`publisherPolicyAssemblyFile`は、このコマンドの結果として作成される発行者ポリシー アセンブリの名前です。 アセンブリ ファイル名は、次の形式に従う必要があります。

  'ポリシー.メジャーナンバー.マイナーナンバー.メインアセンブリ名.dll'

- 引数`keyPairFile`は、キーペアを含むファイルの名前です。 アセンブリと発行者ポリシー アセンブリに同じキー ペアで署名する必要があります。

- この`processorArchitecture`引数は、プロセッサ固有のアセンブリが対象とするプラットフォームを識別します。

  > [!NOTE]
  > 特定のプロセッサ アーキテクチャを対象とする機能は、.NET Framework 2.0 以降で使用できます。

特定のプロセッサ アーキテクチャを対象とする機能は、.NET Framework 2.0 以降で使用できます。 次のコマンドは、 という名前の`policy.1.0.myAssembly`発行者ポリシー ファイルから呼`pub.config`び出される発行者ポリシー アセンブリを作成し、ファイル内のキー`sgKey.snk`ペアを使用してアセンブリに厳密な名前を割り当て、アセンブリが x86 プロセッサ アーキテクチャを対象とすることを指定します。

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

発行者ポリシー アセンブリは、適用先のアセンブリのプロセッサ アーキテクチャと一致する必要があります。 したがって、アセンブリの<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A><xref:System.Reflection.ProcessorArchitecture.MSIL>値が の場合、そのアセンブリの発行者ポリシー アセンブリは を使用`/platform:anycpu`して作成する必要があります。 プロセッサ固有のアセンブリごとに、個別の発行者ポリシー アセンブリを指定する必要があります。

この規則の結果、アセンブリのプロセッサ アーキテクチャを変更するには、バージョン番号のメジャーまたはマイナーコンポーネントを変更して、新しい発行者ポリシー アセンブリに適切なプロセッサ アーキテクチャを提供できるようにする必要があります。 アセンブリに別のプロセッサ アーキテクチャが設定されている場合、古い発行者ポリシー アセンブリはアセンブリにサービスを提供できません。

もう 1 つの結果として、バージョン 2.0 リンカーは、プロセッサ アーキテクチャを常に指定するため、以前のバージョンの .NET Framework を使用してコンパイルされたアセンブリの発行者ポリシー アセンブリを作成できません。

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加する

グローバル[アセンブリ キャッシュ ツール (Gacutil.exe) を](../tools/gacutil-exe-gac-tool.md)使用して、発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加するには

コマンド プロンプトに、次のコマンドを入力します。

```console
gacutil /i publisherPolicyAssemblyFile
```

次のコマンドは`policy.1.0.myAssembly.dll`、グローバル アセンブリ キャッシュに追加します。

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> `/link`引数で指定された元の発行者ポリシー ファイルがアセンブリと同じディレクトリに存在しない限り、発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加することはできません。

## <a name="see-also"></a>関連項目

- [アセンブリを使用したプログラミング](../../standard/assembly/index.md)
- [ランタイムがアセンブリを検索する方法](../deployment/how-the-runtime-locates-assemblies.md)
- [構成ファイルを使用してアプリを構成する方法](index.md)
- [ランタイム設定スキーマ](./file-schema/runtime/index.md)
- [構成ファイル スキーマ](./file-schema/index.md)
- [アセンブリ バージョンのリダイレクト](redirect-assembly-versions.md)
