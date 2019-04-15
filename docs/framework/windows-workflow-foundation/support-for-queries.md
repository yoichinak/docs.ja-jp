---
title: クエリのサポート
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307952"
---
# <a name="support-for-queries"></a>クエリのサポート
SQL Workflow Instance Store は、一連の既知のプロパティをストアに記録します。 ユーザーは、これらのプロパティに基づいてインスタンスのクエリを実行できます。 これらの既知のプロパティの一部を次の一覧に示します。  
  
-   **サイト名: ** サービスが存在する Web サイトの名前。  
  
-   **相対アプリケーション パス: ** Web サイトを基準としたアプリケーションの相対パス。  
  
-   **相対サービス パス: ** アプリケーションを基準としたサービスの相対パス。  
  
-   **サービス名: ** サービスの名前。  
  
-   **サービスの名前空間: ** サービスが使用する名前空間の名称。  
  
-   **現在のコンピューター: **  
  
-   **最後のコンピューター**します。 ワークフロー サービスのインスタンスが最後に実行されたコンピューター。  
  
> [!NOTE]
>  ワークフロー サービス ホストを使用する自己ホスト型のシナリオでは、最後の 4 つのプロパティにのみ値が指定されます。 ワークフロー アプリケーション シナリオでは、最後のプロパティにのみ値が指定されます。  
  
 ワークフロー ランタイムは、最初の 3 つのプロパティの値を指定します。 ワークフロー サービス ホストの値を提供する、**中断の理由**プロパティ。 SQL Workflow Instance Store 自体によって値が提供、**最後に更新されたコンピューター**プロパティ。  
  
 また、SQL Workflow Instance Store の機能により、永続性データベースで値を格納したり、クエリで使用したりするカスタム プロパティを指定することができます。 カスタムの昇格の詳細については、次を参照してください。[ストア拡張](store-extensibility.md)します。  
  
## <a name="views"></a>Views  
 インスタンス ストアには、次のビューがあります。 参照してください[永続性データベース スキーマ](persistence-database-schema.md)の詳細。  
  
### <a name="the-instances-view"></a>Instances ビュー  
 Instances ビューには、次のフィールドがあります。  
  
1. **ID**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>ServiceDeployments ビュー  
 ServiceDeployments ビューには、次のフィールドがあります。  
  
1. **SiteName**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **ServiceName**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>InstancePromotedProperties ビュー  
 InstancePromotedProperties ビューには、次のフィールドがあります。 詳細については、昇格させたプロパティは、次を参照してください。、[ストア拡張](store-extensibility.md)トピック。  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Value #** (さまざまなフィールドから**Value1**に**Value64**)。
