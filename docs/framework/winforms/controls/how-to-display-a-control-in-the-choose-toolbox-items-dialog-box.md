---
title: '方法: 内のコントロールを表示、ツールボックス項目 ダイアログ ボックスの選択'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 191a0848d01eb043420866052b64e2284eb92b49
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720135"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>方法: 内のコントロールを表示、ツールボックス項目 ダイアログ ボックスの選択
を作成およびコントロールを配置することがそれらのコントロールに表示される、**ツールボックス アイテムの選択**] ダイアログ ボックスで、右クリックしたときに表示される、**ツールボックス**選択 **[アイテムの選択**します。 AssemblyFoldersEx の登録手順を使用して、このダイアログ ボックスに表示されるコントロールを有効にすることができます。  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>ツールボックス アイテムの選択 ダイアログ ボックスで、コントロールを表示するには  
  
-   コントロール アセンブリをグローバル アセンブリ キャッシュにインストールします。 詳細については、「[方法 :アセンブリをグローバル アセンブリ キャッシュにインストールする](../../app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     - または -  
  
-   AssemblyFoldersEx の登録手順を使用して、コントロールとその関連付けられたデザイン時アセンブリを登録します。 AssemblyFoldersEx は、サード パーティ ベンダーがサポートされるフレームワークの各バージョンのパスを格納する場所のレジストリの場所です。 デザイン時の解像度は、この参照アセンブリを検索するレジストリの場所で確認できます。 レジストリ スクリプトでは、ツールボックスに表示するコントロールを指定できます。 詳細については、次を参照してください。[カスタム コントロールおよびデザイン時アセンブリを展開する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))します。  
  
## <a name="see-also"></a>関連項目
- [[ツールボックス アイテムの選択] ダイアログ ボックス (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [カスタム コントロールおよびデザイン時アセンブリを展開します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))
- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
- [方法: アセンブリをグローバル アセンブリ キャッシュにインストールする](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [チュートリアル: カスタム コンポーネントでツールボックスが自動的に入力](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
