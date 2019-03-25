---
title: モデル アイテム ツリーのプログラミング
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 9a2af628e10d8b04a91c4f6565dfa1d0d879e870
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714750"
---
# <a name="programming-model-item-tree"></a>モデル アイテム ツリーのプログラミング
このサンプルでは、移動、<xref:System.Activities.Presentation.Model.ModelItem>宣言型データ バインディング、Windows Presentation Foundation (WPF) のツリー ビューを使用してツリーします。

## <a name="sample-details"></a>サンプルの詳細
 <xref:System.Activities.Presentation.Model.ModelItem> ツリーは、編集する基のインスタンスに関するデータを公開するために [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] のインフラストラクチャで使用される抽象表現です。 次の図は、[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]のインフラストラクチャのさまざまな層を表しています。

 ![ワークフロー デザイナーのアーキテクチャ](./media/workflowdesignerarch.JPG "WorkflowDesignerArch")

 <xref:System.Activities.Presentation.Model.ModelItem> は、基になる値へのポインターと、<xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトのコレクションで構成されています。 <xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトはさらに、プロパティの名前や型などのデータと、また別の <xref:System.Activities.Presentation.Model.ModelItem> である値へのポインターで構成されています。 <xref:System.Activities.Presentation.Model.ModelItem> から返される一部の <xref:System.Activities.Presentation.Model.ModelProperty> に対しては、ツリー ビューに正しく表示されるように操作するために値コンバーターが使用されます。 このサンプルでは、次の例のような命令構文を使用して <xref:System.Activities.Presentation.Model.ModelItem> ツリーを命令型プログラミングで操作する方法を示します。

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1.  Visual Studio 2010 で ProgrammingModelItemTree.sln ソリューションを開きます。

2.  選択すると、ソリューションをビルド**ソリューションのビルド**から、**ビルド**メニュー。

3.  F5 キーを押してアプリケーションを実行します。 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] フォームが表示されます。

4.  をクリックして、 **Load WF**を読み込む ボタン、<xref:System.Activities.Presentation.Model.ModelItem>ツリー ビューにバインドします。

5.  クリックすると、 **Change Model Item Tree**ボタン、ツリーにアイテムを追加し、プロパティを設定するには、上記のコードを実行します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Data.IValueConverter>
