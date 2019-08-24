---
title: '方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9a6938b4fe651e13f3ec96642db6027143f1f028
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015897"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する

コントロールを開発および配布するときに、Visual Studio の **[ツールボックスアイテムの選択]** ダイアログボックスにこれらのコントロールを表示することをお勧めします。これは、**ツール**ボックスを右クリックして **[アイテムの選択]** をクリックすると表示されます。 このダイアログボックスにコントロールが表示されるようにするには、AssemblyFoldersEx 登録プロシージャを使用します。

[ツールボックスアイテムの選択] ダイアログボックスにコントロールを表示するには、次のようにします。

- コントロールアセンブリをグローバルアセンブリキャッシュにインストールします。 詳細については、「[方法 :アセンブリをグローバル アセンブリ キャッシュにインストールする](../../app-domains/how-to-install-an-assembly-into-the-gac.md)

  \- または -

- AssemblyFoldersEx 登録プロシージャを使用して、コントロールとそれに関連付けられたデザイン時アセンブリを登録します。 AssemblyFoldersEx は、サードパーティベンダーがサポートする各バージョンのフレームワークのパスを格納するレジストリの場所です。 デザイン時の解決では、このレジストリの場所で参照アセンブリを見つけることができます。 レジストリスクリプトでは、ツールボックスに表示するコントロールを指定できます。

## <a name="see-also"></a>関連項目

- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
- [方法: アセンブリをグローバル アセンブリ キャッシュにインストールする](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [チュートリアル: ツールボックスへのカスタムコンポーネントの自動設定](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
