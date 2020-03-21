---
title: ワークフロー サービス内でのシリアル化の構成
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185343"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>ワークフロー サービス内でのシリアル化の構成
ワークフロー サービスは Windows コミュニケーション ファウンデーション (WCF) サービス<xref:System.Runtime.Serialization.DataContractSerializer>なので、 (既定)<xref:System.Xml.Serialization.XmlSerializer>または . ワークフロー以外のサービスを記述する場合、使用するシリアライザーの型はサービスまたは操作コントラクトで指定されます。 WCF ワークフロー サービスを作成する場合、これらのコントラクトはコードで指定せず、コントラクトの推論によって実行時に生成されます。 コントラクトの推論の詳細については、「[ワークフローでの契約の使用](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)」を参照してください。  シリアライザーは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> プロパティを使用して指定されます。 これは、次の図に示すようにデザイナーで設定できます。  
  
 ![プロパティ ウィンドウでの SerializerOption プロパティを設定します。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
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
  
  ワークフロー サービスにも既知の型を指定できます。 既知の型の詳細については、「[データ コントラクトの既知の型](data-contract-known-types.md)」を参照してください。 既知の型は、デザイナーまたはコードで指定できます。 デザイナーで既知の型を指定するには、次の図に示すように、<xref:System.ServiceModel.Activities.Receive>**アクティビティのプロパティ ウィンドウ**で KnownTypes プロパティの横にある省略記号ボタンをクリックします。
  
 ![[既知の種類] プロパティ ダイアログ ボックスのスクリーンショット。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 これにより、既知の型を検索および指定できる型コレクション エディタが表示されます。  
  
 ![型コレクション エディターのスクリーンショット。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 [**新しい型の追加]** リンクをクリックし、ドロップダウンを使用して、既知の型コレクションに追加する型を選択または検索します。 既知の型をコードで指定するには、次の例に示すように <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> プロパティを使用します。  
  
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
