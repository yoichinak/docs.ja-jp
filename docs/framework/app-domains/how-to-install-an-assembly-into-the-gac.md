---
title: '方法: アセンブリをグローバル アセンブリ キャッシュにインストールする'
ms.date: 02/05/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 233a7803cb59f9bfeac15d293dc3fb5a0db449c9
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903755"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>方法: アセンブリをグローバル アセンブリ キャッシュにインストールする

グローバル アセンブリ キャッシュ (GAC) には、複数のアプリケーションで共有されるアセンブリが格納されています。 次のコンポーネントのいずれかを使用して、アセンブリを[グローバル アセンブリ キャッシュ](gac.md)にインストールします。 
- [Windows インストーラー](#windows-installer)
- [グローバル アセンブリ キャッシュ ツール](#global-assembly-cache-tool)

> [!IMPORTANT]
> GAC にインストールできるのは、厳密な名前付きのアセンブリだけです。 厳密な名前付きのアセンブリを作成する方法については、「[方法:厳密な名前でアセンブリに署名する](how-to-sign-an-assembly-with-a-strong-name.md)」を参照してください。

## <a name="windows-installer"></a>Windows インストーラー

アセンブリをグローバル アセンブリ キャッシュに追加するための推奨する方法は、[Windows インストーラー](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)(Windows インストール エンジン) です。 Windows インストーラーを使用すると、グローバル アセンブリ キャッシュ内のアセンブリの参照カウントが示されるなどの利点があります。 Windows インストーラー用のインストーラー パッケージを作成するには、[Visual Studio 2017 用 WiX Toolset 拡張機能](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)を使用します。

## <a name="global-assembly-cache-tool"></a>グローバル アセンブリ キャッシュ ツール

[グローバル アセンブリ キャッシュ ツール (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) を使用して、アセンブリをグローバル アセンブリ キャッシュに追加したり、グローバル アセンブリ キャッシュの内容を表示したりできます。

   > [!NOTE]
   > *Gacutil.exe* は、開発のみを目的としています。 これは運用環境のアセンブリをグローバル アセンブリ キャッシュにインストールするのには使用しないでください。

*gacutil.exe* を使用して GAC にアセンブリをインストールするための構文は、次のとおりです。

```console
gacutil -i <assembly name>
```

このコマンドの *\<assembly name>* は、グローバル アセンブリ キャッシュにインストールされるアセンブリの名前です。

システム パスに *gacutil.exe* が含まれていない場合は、[開発者コマンド プロンプト for VS *\<バージョン>*](../tools/developer-command-prompt-for-vs.md) を使用します。

ファイル名 *hello.dll* のアセンブリをグローバル アセンブリ キャッシュにインストールする例を次に示します。

```console
gacutil -i hello.dll
```

> [!NOTE]
> 以前のバージョンの .NET Framework では、Windows のシェル拡張機能である *Shfusion.dll* により、ファイル エクスプローラーにアセンブリをドラッグしてインストールすることができました。 .NET Framework 4 以降では、*Shfusion.dll* は廃止されました。

## <a name="see-also"></a>関連項目

- [アセンブリとグローバル アセンブリ キャッシュの使用](working-with-assemblies-and-the-gac.md)
- [方法: グローバル アセンブリ キャッシュからアセンブリを削除する](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../tools/gacutil-exe-gac-tool.md)
- [方法: 厳密な名前でアセンブリに署名する](how-to-sign-an-assembly-with-a-strong-name.md)
