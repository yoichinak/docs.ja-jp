---
title: '方法: 公開キーと秘密キーのキー ペアを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71eaaa85b8bd287c37f59116e75cf99b030d63ac
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297838"
---
# <a name="how-to-create-a-public-private-key-pair"></a>方法: 公開キーと秘密キーのキー ペアを作成する

アセンブリに厳密な名前で署名するには、公開/秘密キーの組み合わせが必要です。 このような公開キーと秘密キーからなる暗号鍵の組み合わせがコンパイル時に利用され、厳密な名前が付いたアセンブリが作成されます。 キーの組み合わせは[厳密名ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を利用して作成できます。 キー ペア ファイルには通常、.snk 拡張子が与えられます。

> [!NOTE]
> Visual Studio では、C# と Visual Basic のプロジェクト プロパティ ページに **[署名]** タブがあります。このタブで、Sn.exe を使用することなく、既存のキー ファイルを選択したり、新しいキー ファイルを生成したりすることができます。 Visual C++ では、**[プロパティ ページ]** ウィンドウの **[構成プロパティ]** セクションの **[リンカー]** セクションの **[詳細設定]** プロパティ ページで既存のキー ファイルの場所を指定できます。 Visual Studio 2005 より、キー ファイル ペアを特定する <xref:System.Reflection.AssemblyKeyFileAttribute> 属性を使用できなくなりました。

## <a name="to-create-a-key-pair"></a>キー ペアを作成するには

1. コマンド プロンプトに次のコマンドを入力します。

     **sn –k** \<*ファイル名*>

     このコマンドでは、*ファイル名*はキー ペアを含む出力ファイルの名前になります。

 次の例では、`sgKey.snk` という名前のキー ペアが作成されます。

```
sn -k sgKey.snk
```

 アセンブリに遅延署名する予定であり、キー ペア全体を制御する (テスト シナリオの範囲を超えることは予期されない) のであれば、次のコマンドを利用してキー ペアを生成し、それから個別ファイルに公開キーを抽出できます。 最初に、キー ペアを作成します。

```
sn -k keypair.snk
```

 次に、キー ペアから公開キーを抽出し、それを個別ファイルにコピーします。

```
sn -p keypair.snk public.snk
```

 キー ペアを作成したら、厳密な名前の署名ツールで見つけられる場所にファイルを置く必要があります。

 厳密な名前でアセンブリに署名すると、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) は、現在のディレクトリと出力ディレクトリを基準にしてキー ファイルを検索します。 コマンド ライン コンパイラを使用する場合は、コード モジュールを格納する現在のディレクトリにキーをコピーするだけで十分です。

 プロジェクト プロパティに **[署名]** タブがない以前のバージョンの Visual Studio を利用している場合、キー ファイルの推奨場所はファイル属性が次のように指定されたプロジェクト ディレクトリです。

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a>関連項目

- [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
