---
title: タスク 1:新しい Windows Presentation Foundation アプリケーションの作成
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 44152f0af73b134218cd975d93e186166b1e57ae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665320"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>タスク 1:新しい Windows Presentation Foundation アプリケーションの作成
このタスクでは、WPF Application Visual Studio テンプレートを使用して空の Windows Presentation Foundation (WPF) アプリケーションを作成し、適切な参照を追加[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]ワークフロー アセンブリ。  
  
### <a name="to-create-the-wpf-application-project"></a>WPF アプリケーション プロジェクトを作成するには  
  
1. Visual Studio を起動し、**ファイル**メニューで、**新規**、順にクリックします**プロジェクト**します。  
  
2. **新しいプロジェクト** ダイアログ ボックスで、いずれかを選択**Visual C#** または**Visual Basic**から、**インストールされたテンプレート**左側のウィンドウボックスのあります。 好みの言語が表示されない場合は、検索**他の言語**します。  
  
3. 選択**Windows**で、**インストールされたテンプレート**ウィンドウ。  
  
4. 上部のペインのことを確認します (既定値) **.NET Framework 4**し、ドロップダウン リスト ボックスで、選択したされました**WPF アプリケーション**します。  
  
5. プロジェクトの名前を設定**HostingApplication**ウィンドウの下部にあります。  
  
6. ソリューション名を設定**RehostingTheDesigner**します。  
  
7. クリックして**OK**アプリケーション プロジェクトを作成します。 Visual Studio では、アプリケーションの基本的な WPF UI を作成し、適切な XAML と分離コード ファイルが含まれています。  
  
8. 参照を追加**WorkflowModel**アセンブリ。 この場合に**ソリューション エクスプ ローラー**を右クリックし、 **HostingApplication**順に選択して**参照の追加**。  
  
9. **参照の追加**ダイアログ ボックスで、をクリックして、 **.NET**  タブ、CTRL キーを押し、次のアセンブリを選択し、順にクリックします**OK**:  
  
    - System.Activities  
  
    - System.Activities.Presentation  
  
    - System.Activities.Core.Presentation  
  
10. **[OK]** をクリックします。  
  
11. 参照してください[タスク 2。ワークフロー デザイナーのホスティング](task-2-host-the-workflow-designer.md)をワークフロー デザイナーのデザイン キャンバスをホストする方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)
- [タスク 2:ワークフロー デザイナーをホスティングします。](task-2-host-the-workflow-designer.md)
