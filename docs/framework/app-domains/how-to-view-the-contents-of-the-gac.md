---
title: '方法: グローバル アセンブリ キャッシュの内容を表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c319c5f7c9bb808b2ce7ee10178722287e456339
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486430"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>方法: グローバル アセンブリ キャッシュの内容を表示する

[グローバル アセンブリ キャッシュ ツール (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュ (GAC) の内容を表示できます。

## <a name="view-the-assemblies-in-the-gac"></a>GAC 内のアセンブリを表示する

グローバル アセンブリ キャッシュ内のアセンブリの一覧を表示するには、[Visual Studio 用開発者コマンド プロンプト](../tools/developer-command-prompt-for-vs.md)を開いて次のコマンドを入力します。

```shell
gacutil -l
```

- または -

```shell
gacutil /l
```

> [!NOTE]
> 以前のバージョンの .NET Framework では、Windows のシェル拡張機能である [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) により、エクスプローラーでグローバル アセンブリ キャッシュを表示することができました。 .NET Framework 4 以降、Shfusion.dll は廃止されましたが、互換性のために残されています。

## <a name="see-also"></a>関連項目

- [アセンブリとグローバル アセンブリ キャッシュの使用](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../tools/gacutil-exe-gac-tool.md)
