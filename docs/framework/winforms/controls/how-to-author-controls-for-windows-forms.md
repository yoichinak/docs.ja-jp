---
title: '方法: Windows フォームのコントロールを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: 0804b9824b84a32bdd79c763031a3de4ffa54099
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039876"
---
# <a name="how-to-author-controls-for-windows-forms"></a>方法: Windows フォームのコントロールを作成する

コントロールは、ユーザーとプログラムの間のグラフィカルなリンクを表します。 コントロールは、データの提供または処理、ユーザー入力の受け付け、イベントへの応答、ユーザーとアプリケーションを接続する他の任意の数の関数の実行を行うことができます。 コントロールは、基本的にグラフィカル インターフェイスを持つコンポーネントであるため、ユーザーとの対話だけでなく、コンポーネントが実行するあらゆる機能を果たします。 コントロールは特定の目的に使用するために作成します。コントロールの作成は、まったく別のプログラミング タスクです。 このことを念頭に、次の手順では、コントロールの作成手順の概要を示します。 個々の手順のリンクで追加情報を提供します。

> [!NOTE]
> Web フォームで使用するカスタム コントロールを作成する場合は、「[カスタム ASP.NET サーバー コントロールの開発](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))」を参照してください。

## <a name="to-author-a-control"></a>コントロールを作成するには

1. コントロールで何を実行するか、またはアプリケーション内のどのような役割を果たすかを決定します。 考慮すべき要素は次のとおりです。

    - どのようなグラフィカル インターフェイスが必要か。

    - このコントロールでユーザーとの間で具体的にどのような対話を処理するか。

    - 必要とする機能が既存のコントロールによって提供されるかどうか。

    - 複数の Windows フォーム コントロールを組み合わせることによって必要とする機能を実現できるかどうか。

2. コントロール用にオブジェクト モデルが必要な場合は、オブジェクト モデル全体に機能を配布する方法を決定し、コントロールと下位オブジェクトの間で機能を分割します。 複合コントロールを計画している場合や、複数の機能を組み込む場合は、オブジェクト モデルが役立つ可能性があります。

3. 必要なコントロールの種類 (ユーザー コントロール、カスタム コントロール、継承された Windows フォーム コントロールなど) を特定します。 詳細については、「[コントロールの種類に関するアドバイス](control-type-recommendations.md)」と「[さまざまなカスタム コントロール](varieties-of-custom-controls.md)」を参照してください。

4. 機能をプロパティ、メソッド、およびコントロールとその下位オブジェクトまたは従属構造体のイベントとして表現し、適切なアクセス レベル (たとえば、public、protected など) を割り当てます。

5. コントロールのカスタム描画が必要な場合は、そのコードを追加します。 詳細については、「[コントロールのカスタム描画およびレンダリング](custom-control-painting-and-rendering.md)」を参照してください。

6. コントロールがから<xref:System.Windows.Forms.UserControl>継承されている場合は、コントロールプロジェクトをビルドし、 **UserControl テストコンテナー**で実行することによって、実行時の動作をテストできます。 詳細については、「[方法 :UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)の実行時の動作をテストします。

7. Windows アプリケーションなどの新しいプロジェクトを作成してコンテナーに配置することで、コントロールをテストしてデバッグすることができます。 このプロセスは、チュートリアルの[一部として示されています。Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)による複合コントロールの作成。

8. 各機能を追加するときは、テスト プロジェクトに機能を追加して新しい機能を実行します。

9. 繰り返して、デザインを調整します。

10. コントロールをパッケージ化してデプロイします。 詳細については、「 [Visual Studio での配置の概要](/visualstudio/deployment/deploying-applications-services-and-components)」を参照してください。

## <a name="see-also"></a>関連項目

- [チュートリアル: Visual Basic による複合コントロールの作成](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [チュートリアル: Visual Basic を使用した Windows フォームコントロールからの継承](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [方法: UserControl クラスを継承する](how-to-inherit-from-the-usercontrol-class.md)
- [方法: コントロールクラスから継承する](how-to-inherit-from-the-control-class.md)
- [方法: 既存の Windows フォームコントロールから継承する](how-to-inherit-from-existing-windows-forms-controls.md)
- [方法: UserControl の実行時の動作をテストする](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
