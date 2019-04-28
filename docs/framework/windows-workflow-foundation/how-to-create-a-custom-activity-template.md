---
title: '方法: カスタム アクティビティ テンプレートを作成する'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: ee6f249092c5cf8643e3c9bfd15d32e77791d8bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773618"
---
# <a name="how-to-create-a-custom-activity-template"></a>方法: カスタム アクティビティ テンプレートを作成する

カスタム複合アクティビティなどのアクティビティの構成のカスタマイズには、カスタム アクティビティ テンプレートが使用されるため、手動で各アクティビティを個別に作成し、そのプロパティおよびその他の設定を構成する必要はありません。 これらのカスタム テンプレートで使用できる、**ツールボックス**上、[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]または元のユーザーに画面にドラッグできる、構成済みのデザイン、再ホストされたデザイナーから。 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] このようなテンプレートの良い例が付属しています。 [SendAndReceiveReply テンプレート デザイナー](/visualstudio/workflow-designer/sendandreceivereply-template-designer)と[ReceiveAndSendReply テンプレート デザイナー](/visualstudio/workflow-designer/receiveandsendreply-template-designer)で、[メッセージング アクティビティ デザイナー](/visualstudio/workflow-designer/messaging-activity-designers)カテゴリ。

 このトピックの最初の手順についてのカスタム アクティビティ テンプレートを作成する方法を説明します、**遅延**アクティビティと 2 番目の手順で使用できるようにする方法ではについて簡単に説明を[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]カスタム テンプレートが機能することを確認します。

 カスタム アクティビティ テンプレートに <xref:System.Activities.Presentation.IActivityTemplateFactory> を実装する必要があります。 このインターフェイスには単一の <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> メソッドがあり、このメソッドを使用して、テンプレートで使用されるアクティビティ インスタンスを作成および構成できます。

## <a name="to-create-a-template-for-the-delay-activity"></a>Delay アクティビティのテンプレートを作成するには

1. Visual Studio 2010 を起動します。

2. **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#** プロジェクトまたは**Visual Basic**に応じてグループ化、優先する言語。

4. **テンプレート**ペインで、**アクティビティ ライブラリ**します。

5. **名前**ボックスに、入力`DelayActivityTemplate`します。

6. 既定値のまま、**場所**と**ソリューション名**テキスト ボックス、およびクリック **[ok]** します。

7. DelayActivityTemplate プロジェクトの参照ディレクトリを右クリックして**ソリューション エクスプ ローラー**選択**参照の追加**を開く、**参照の追加** ダイアログ ボックス。

8. 移動して、 **.NET**タブおよび選択**PresentationFramework**から、**コンポーネント名**をクリックし、左の列**OK**参照を追加するにはPresentationFramework.dll ファイル。

9. この手順を繰り返して、System.Activities.Presentation.dll ファイルと WindowsBase.dll ファイルへの参照を追加します。

10. DelayActivityTemplate プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**し**新しい項目の**を開く、 **の新しい項目の追加** ダイアログ ボックス。

11. 選択、**クラス**テンプレート、MyDelayTemplate、という名前をクリックして**OK**します。

12. MyDelayTemplate.cs ファイルを開き、次のステートメントを追加します。

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. 次のコードを使用して、<xref:System.Activities.Presentation.IActivityTemplateFactory> クラスを持つ `MyDelayActivity` を実装します。 これにより、10 秒間の遅延が構成されます。

    ```
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. 選択**ソリューションのビルド**から、**ビルド**DelayActivityTemplate.dll ファイルを生成するメニュー。

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>ワークフロー デザイナーでテンプレートを利用できるようにするには

1. DelayActivityTemplate ソリューションを右クリックして**ソリューション エクスプ ローラー**選択**追加**し**新しいプロジェクト**を開く、 **の新しいプロジェクトの追加**  ダイアログ ボックス。

2. 選択、**ワークフロー コンソール アプリケーション**テンプレート、という名前を付けます`CustomActivityTemplateApp`、順にクリックします**OK**します。

3. CustomActivityTemplateApp プロジェクトの参照ディレクトリを右クリックして**ソリューション エクスプ ローラー**選択**参照の追加**を開く、**参照の追加**ダイアログボックス。

4. 移動、**プロジェクト**タブおよび選択**DelayActivityTemplate**から、**プロジェクト名**をクリックし、左の列**OK**を追加する、最初の手順で作成した DelayActivityTemplate.dll ファイルへの参照します。

5. CustomActivityTemplateApp プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**ビルド**アプリケーションをコンパイルします。

6. CustomActivityTemplateApp プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**します。

7. 選択**デバッグなしで開始**から、**デバッグ**メニューとキーを押して任意のキーを cmd.exe ウィンドウから入力を求められたらを続行します。

8. Workflow1.xaml ファイルを開き、開く、**ツールボックス**します。

9. 検索、 **MyDelayActivity**テンプレート、 **DelayActivityTemplate**カテゴリ。 デザイン サーフェイスにドラッグします。 確認、**プロパティ**ウィンドウを`Duration`プロパティが 10 秒に設定されています。

## <a name="example"></a>例
 MyDelayActivity.cs ファイルには次のコードが含まれます。

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a>関連項目

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [ワークフロー デザイン操作のカスタマイズ](customizing-the-workflow-design-experience.md)