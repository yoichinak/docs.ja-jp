---
title: ワークフロー サービス内でのシリアル化の構成
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843931"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>ワークフロー サービス内でのシリアル化の構成
ワークフロー サービスは、Windows Communication Foundation (WCF) サービスをそのため、オプションのいずれかを使用して、、 <xref:System.Runtime.Serialization.DataContractSerializer> (既定値) または<xref:System.Xml.Serialization.XmlSerializer>します。 ワークフロー以外のサービスを記述する場合、使用するシリアライザーの型はサービスまたは操作コントラクトで指定されます。 WCF ワークフロー サービスを作成するときに、コードでは、これらのコントラクトを指定しないが、コントラクト推論で実行時に生成されます。 コントラクト推論の詳細については、次を参照してください。[ワークフローを使用してコントラクト](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)します。  シリアライザーは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> プロパティを使用して指定されます。 これは、次の図に示すようにデザイナーで設定できます。  
  
 ![[プロパティ] ウィンドウには、SerializerOption プロパティを設定します。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 シリアライザーは、次の例に示すようにコードで設定することもできます。  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  ワークフロー サービスにも既知の型を指定できます。 既知の型の詳細については、次を参照してください。 [Data Contract Known Types](data-contract-known-types.md)します。 既知の型は、デザイナーまたはコードで指定できます。 デザイナーで既知の型を指定するで KnownTypes プロパティの横にある省略記号ボタンをクリックして、**プロパティ ウィンドウ**の<xref:System.ServiceModel.Activities.Receive>アクティビティの次の図に示すようにします。   
  
 ![KnownTypes プロパティのダイアログ ボックスのスクリーン ショット。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 これと既知の型を指定して検索することができる型コレクション エディターが表示されます。  
  
 ![型のコレクション エディターのスクリーン ショット。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 をクリックして、**新しいタイプの追加**リンクし、既知の型のコレクションに追加する型の選択や検索ドロップダウンを使用します。 既知の型をコードで指定するには、次の例に示すように <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> プロパティを使用します。  
  
```csharp
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```
