---
title: アクティビティ拡張機能の使用
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321290"
---
# <a name="using-activity-extensions"></a>アクティビティ拡張機能の使用
アクティビティは、ワークフローで明示的にモデル化されていない追加機能の提供をホストに許可するワークフロー アプリケーション拡張機能と相互作用することができます。  ここでは、アクティビティの実行回数をカウントする拡張機能を作成および使用する方法について説明します。

### <a name="to-use-an-activity-extension-to-count-executions"></a>実行回数をカウントするアクティビティ拡張機能を使用するには

1. Visual Studio 2010 を開きます。 選択**新しい**、**プロジェクト**します。 下、 **Visual c#** ノードの **ワークフロー**します。  選択**ワークフロー コンソール アプリケーション**テンプレートの一覧から。 プロジェクトに `Extensions` という名前を付けます。 **[OK]** をクリックして、プロジェクトを作成します。

2. 追加、`using`の Program.cs ファイル内のステートメント、 **System.Collections.Generic**名前空間。

    ```
    using System.Collections.Generic;
    ```

3. という名前の新しいクラスを作成、Program.cs ファイルで**ExecutionCountExtension**します。 次のコードでは、インスタンス Id を追跡するワークフロー拡張機能とその**登録**メソッドが呼び出されます。

    ```
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. 使用するアクティビティを作成、 **ExecutionCountExtension**します。 次のコードを取得するアクティビティを定義する、 **ExecutionCountExtension**オブジェクトを実行時と呼び出しからその**登録**アクティビティの実行時のメソッド。

    ```
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. アクティビティでは、実装、 **Main** program.cs ファイルのメソッド。 次のコードには、2 つの異なるワークフローを生成し、各ワークフローを数回実行して、拡張機能に含まれる結果のデータを表示するメソッドが含まれています。

    ```
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
