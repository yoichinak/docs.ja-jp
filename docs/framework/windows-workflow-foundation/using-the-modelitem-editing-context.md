---
title: ModelItem 編集コンテキストの使用
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a2628bbbf2f6684e5d484b05cd5a2ac622f3b664
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669499"
---
# <a name="using-the-modelitem-editing-context"></a>ModelItem 編集コンテキストの使用
<xref:System.Activities.Presentation.Model.ModelItem> 編集コンテキストは、ホスト アプリケーションがデザイナーとの通信に使用するオブジェクトです。 <xref:System.Activities.Presentation.EditingContext> は使用できる 2 つのメソッド <xref:System.Activities.Presentation.EditingContext.Items%2A> と <xref:System.Activities.Presentation.EditingContext.Services%2A> を公開します。  
  
## <a name="the-items-collection"></a>Items コレクション  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> コレクションは、ホストとデザイナー間で共有されるデータ、またはすべてのデザイナーで使用可能なデータへのアクセスに使用されます。 このコレクションには、<xref:System.Activities.Presentation.ContextItemManager> クラスを介してアクセスされる次の機能があります。  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Services コレクション  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> コレクションは、デザイナーとホスト間の対話に使用されるサービス、またはすべてのデザイナーで使用されるサービスへのアクセスに使用されます。 このコレクションには、重要な次のメソッドがあります。  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>デザイナーへのアクティビティの割り当て  
 アクティビティで使用されるデザイナーを指定するには、Designer 属性が使用されます。  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>サービスの作成  
 デザイナーとホスト間の情報のコンジットとして機能するサービスを作成するには、インターフェイスと実装を作成する必要があります。 インターフェイスはサービスのメンバーを定義するために <xref:System.Activities.Presentation.ServiceManager.Publish%2A> メソッドによって使用され、実装にはサービスのロジックが含まれます。 次のコード例では、サービス インターフェイスと実装が作成されます。  
  
```  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {   
                DisplayName + " One",   
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a>サービスの公開  
 デザイナーでサービスを使用するには、最初に <xref:System.Activities.Presentation.ServiceManager.Publish%2A> メソッドを使用してホストで公開する必要があります。  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>サービスの定期受信  
 デザイナーは、<xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> メソッドの <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> メソッドを使用してサービスにアクセスします。 次のコード スニペットは、サービスを定期受信する方法を示しています。  
  
```  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;   
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a>Items コレクションを使用したデータの共有  
 Items コレクションの使用は Services コレクションの使用と似ていますが、Publish の代わりに <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> が使用されます。 このコレクションは、複雑な機能よりも、デザイナーとホスト間での単純なデータの共有に適しています。  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext ホスト項目およびサービス  
 .NET Framework では、さまざまな組み込みの項目とサービスの編集コンテキストを使用してアクセスを提供します。  
  
 項目:  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>:式エディター) などのコントロールのワークフロー内で使用される参照先ローカル アセンブリの一覧を管理します。  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>:デザイナーが読み取り専用状態かどうかを示します。  
  
- <xref:System.Activities.Presentation.View.Selection>:現在選択されているオブジェクトのコレクションを定義します。  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>:現在の編集セッションが基づくファイルについてを説明します。  
  
 サービス:  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>:プロパティは、現在のインスタンスに追加することができますを使用して<xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>します。  
  
- <xref:System.Activities.Presentation.View.DesignerView>:デザイナー キャンバスのプロパティにアクセスをできます。  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>:更新するツールボックスの内容を使用できます。  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>:カスタム指定されたサービスの実装とデザイナー コマンド (コンテキスト メニューなど) を統合するために使用します。  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>:デザイナーのデバッガーの機能を提供します。  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>:式エディター ダイアログへのアクセスを提供します。  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>:統合ヘルプ機能を備えた、デザイナーを提供します。  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>:使用して検証エラーにアクセスできる<xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>します。  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>:データを格納および取得の内部のサービスを提供します。 このサービスは、.NET Framework で内部的に使用し、外部使用のためのものではありません。  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>:XAML 読み込みエラー コレクションを使用して、アクセスできるように<xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>します。  
  
- <xref:System.Activities.Presentation.Services.ModelService>:編集されているワークフローのモデルと対話するデザイナーが使用されます。  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>:使用してモデル アイテム ツリーのルートへのアクセスを提供します。<xref:System.Activities.Presentation.Model.ModelItem.Root%2A>します。  
  
- <xref:System.Activities.Presentation.UndoEngine>:提供元に戻すと、機能を再実行します。  
  
- <xref:System.Activities.Presentation.Services.ViewService>:視覚的要素を基になるモデル アイテムにマップします。  
  
- <xref:System.Activities.Presentation.View.ViewStateService>:ストアでは、モデル項目の状態を表示します。  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>:仮想コンテナーの UI 動作をカスタマイズするために使用します。  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>:登録およびイベント通知用のデリゲートを登録解除するために使用します。 ウィンドウ所有者も設定できます。
