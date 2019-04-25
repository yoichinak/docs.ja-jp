---
title: CodeActivity クラスを使用したワークフロー アクティビティの作成
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 549acec8b8101312d48bd20e63a4a988b798ff38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767397"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>CodeActivity クラスを使用したワークフロー アクティビティの作成
<xref:System.Activities.CodeActivity> を継承して作成されたアクティビティは、<xref:System.Activities.CodeActivity.Execute%2A> メソッドをオーバーライドすることで強制的な基本動作を実装できます。

## <a name="using-codeactivitycontext"></a>CodeActivityContext の使用
 ワークフロー ランタイムの機能は、<xref:System.Activities.CodeActivity.Execute%2A> 型の `context` パラメーターを使用して、<xref:System.Activities.CodeActivityContext> メソッド内からアクセスできます。 <xref:System.Activities.CodeActivityContext> を介して、以下のような機能を使用できます。

-   変数と引数の値を取得および設定。

-   <xref:System.Activities.CodeActivityContext.Track%2A> を使用したカスタムの追跡機能。

-   <xref:System.Activities.CodeActivityContext.GetProperty%2A> を使用したアクティビティの実行プロパティへのアクセス。

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>CodeActivity を継承するカスタム アクティビティを作成するには

1. Visual Studio 2010 を開きます。

2. 選択**ファイル**、**新しい**、し**プロジェクト**します。 選択**Workflow 4.0**  **Visual c#** で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。 選択**アクティビティ ライブラリ**で、**テンプレート**ウィンドウ。 新しいプロジェクトに HelloActivity という名前を付けます。

3. HelloActivity プロジェクトの Activity1.xaml を右クリックして**削除**します。

4. HelloActivity プロジェクトを右クリックして**追加**、し**クラス**します。 新しいクラスに HelloActivity.cs という名前を付けます。

5. HelloActivity.cs ファイルで、次の `using` ディレクティブを追加します。

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. クラス宣言に基本クラスを追加することにより、新しいクラスで <xref:System.Activities.CodeActivity> から継承します。

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <xref:System.Activities.CodeActivity.Execute%2A> メソッドを追加して、このクラスに機能を追加します。

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <xref:System.Activities.CodeActivityContext> を使用して追跡レコードを作成します。

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
