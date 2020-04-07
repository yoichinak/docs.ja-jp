---
title: 自己完結型アプリケーションのトリミング
description: 自己完結型アプリケーションをトリミングしてサイズを縮小する方法について説明します。 .NET Core は、自己完結型で公開されているアプリケーションでランタイムをバンドルし、通常は必要以上のランタイムを含んでいます。
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665621"
---
# <a name="trim-self-contained-deployments-and-executables"></a>自己完結型の展開と実行可能ファイルのトリミング

自己完結型アプリケーションを公開する場合、.NET Core ランタイムにはアプリケーションもバンドルされます。 このバンドルにより、パッケージ アプリケーションに大量のコンテンツが追加されます。

アプリケーションの展開では、多くの場合、サイズが重要な要素になります。 通常は、パッケージ アプリケーションのサイズをなるべく小さく保つことが、アプリケーション開発者の目標となります。

アプリケーションの複雑さによっては、アプリケーションの実行にランタイムのサブセットだけが必要となります。 このようなランタイムの未使用部分は不要であり、パッケージ化されたアプリケーションから削除することができます。

> [!NOTE]
> トリミングは .NET Core 3.1 の実験的な機能であり、自己完結型で公開されるアプリケーションで_のみ_使用できます。

## <a name="trim-your-application"></a>アプリケーションをトリミングする

次の例は、[dotnet publish](../tools/dotnet-publish.md) コマンドを使用してアプリケーションをトリミングする方法を示しています。

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

トリミング機能は、アプリケーション バイナリを調べて、必要なランタイム アセンブリのグラフを検出し、構築することで機能します。 参照されていないその他のランタイム アセンブリはトリミングされます。

## <a name="trimming-issues-when-using-reflection"></a>リフレクションを使用するときのトリミングの問題

トリミング機能が参照の検出に失敗するシナリオがあります。 たとえば、リフレクションを使用するアプリケーションでは、アセンブリの依存関係が実行時にのみ認識されるため、この問題が発生する可能性があります。

トリミングは、リフレクションの使用が、直接参照されていないランタイム アセンブリに依存している場合にのみ問題になります。 お使いのアプリケーション コードがリフレクションを直接使用していない可能性がありますが、参照しているサードパーティ アセンブリがそれを使用している可能性があります。

コードがリフレクションを通じて API を参照していて、その API を含むアセンブリをリンカーでトリミングしたくない場合は、プロジェクト ファイルを変更して、トリミング プロセスからアセンブリを除外することができます。 次の例は、`System.Security` という名前のアセンブリがトリミングされないようにする方法を示しています。

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a>関連項目

- [.NET Core アプリケーションの展開](index.md)
