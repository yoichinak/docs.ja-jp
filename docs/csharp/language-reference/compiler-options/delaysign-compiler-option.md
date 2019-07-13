---
title: -delaysign (C# コンパイラ オプション)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 1d49733531507fc80165e034fde1969305cfd2e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681730"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# コンパイラ オプション)

このオプションを使用すると、出力ファイルに署名用のスペースが予約され、デジタル署名を後で追加できるようになります。

## <a name="syntax"></a>構文

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>引数

`+` &#124; `-`

完全署名されたアセンブリを作成する場合は、**-delaysign-** を使用します。 アセンブリに公開キーだけを含める場合は、**-delaysign+** を使用します。 既定値は **-delaysign-** です。

## <a name="remarks"></a>コメント

**-delaysign** オプションは、[-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) または [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) と共に使用しない場合、無効になります。

**-delaysign** オプションと **-publicsign** オプションは相互に排他的です。

アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。 その処理により、マニフェストを含むファイルに格納されるデジタル署名が作成されます。 アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。

たとえば、**-delaysign+** を指定すると、テスト時にはアセンブリをグローバル キャッシュに格納できます。 テスト後に、[アセンブリ リンカー](../../../framework/tools/al-exe-assembly-linker.md) ユーティリティを使用してアセンブリに秘密キーを配置することにより、そのアセンブリに完全署名できます。

詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)」および「[アセンブリへの遅延署名](../../../framework/app-domains/delay-sign-assembly.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ]** ページを開きます。
1. **[遅延署名のみ]** プロパティを変更します。

このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」をご覧ください。

## <a name="see-also"></a>関連項目

- [C# の -publicsign オプション](publicsign-compiler-option.md)
- [C# コンパイラ オプション](index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
