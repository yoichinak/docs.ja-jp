---
title: モデル アイテム ツリーのプログラミング
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038172"
---
# <a name="programming-model-item-tree"></a>モデル アイテム ツリーのプログラミング
このサンプルでは、Windows Presentation Foundation ( <xref:System.Activities.Presentation.Model.ModelItem> WPF) ツリービューの宣言型データバインディングを使用してツリー内を移動する方法を示します。

## <a name="sample-details"></a>サンプルの詳細
 <xref:System.Activities.Presentation.Model.ModelItem> ツリーは、編集する基のインスタンスに関するデータを公開するために [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] のインフラストラクチャで使用される抽象表現です。 次の図は、[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]のインフラストラクチャのさまざまな層を表しています。

 ![ワークフローデザイナーアーキテクチャを示す図。](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem> は、基になる値へのポインターと、<xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトのコレクションで構成されています。 <xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトはさらに、プロパティの名前や型などのデータと、また別の <xref:System.Activities.Presentation.Model.ModelItem> である値へのポインターで構成されています。 <xref:System.Activities.Presentation.Model.ModelItem> から返される一部の <xref:System.Activities.Presentation.Model.ModelProperty> に対しては、ツリー ビューに正しく表示されるように操作するために値コンバーターが使用されます。 このサンプルでは、次の例のような命令構文を使用して <xref:System.Activities.Presentation.Model.ModelItem> ツリーを命令型プログラミングで操作する方法を示します。

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2010 で ProgrammingModelItemTree ソリューションを開きます。

2. **[ビルド]** メニューの **[ソリューションのビルド]** を選択して、ソリューションをビルドします。

3. F5 キーを押してアプリケーションを実行します。 WPF フォームが表示されます。

4. **[WF の読み込み]** ボタンをクリック<xref:System.Activities.Presentation.Model.ModelItem>すると、が読み込まれ、ツリービューにバインドされます。

5. **[モデル項目ツリーの変更]** ボタンをクリックすると、前のコードが実行され、ツリーに項目が追加され、プロパティが設定されます。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.IValueConverter>
