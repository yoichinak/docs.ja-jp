---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: b6221e93f10b87a368bd594932a8c36ae14df8f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772831"
---
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceBehaviorAttribute クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceBehaviorAttribute クラスには、次のプロパティがあります。  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 クライアントが出力セッションを閉じるときにセッションを自動的に閉じるかどうかを示します。  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 データ型: string  
アクセスの種類:読み取り専用  
  
 サービスで、1 つのスレッド、複数のスレッド、または再入呼び出しをサポートするかどうかを示します。  
  
### <a name="configurationname"></a>ConfigurationName  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 サービス構成の名前。  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 不明なシリアル化データをネットワークで送信するかどうかを指定します。  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージド例外情報を含めるかどうかを指定します。  
  
### <a name="instancecontextmode"></a>InstanceContextMode  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 新しいサービス オブジェクトを作成するタイミングを指定します。  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 1 つのシリアル化されたオブジェクトで許可される項目の最大数。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 WSDL でのサービスの名前属性。  
  
### <a name="namespace"></a>名前空間  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 WSDL でのサービスのターゲット名前空間。  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 現在のトランザクションの完了時に、サービス オブジェクトをリサイクルするかどうかを指定します。  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 現在のセッションの終了時に、保留中のトランザクションを完了するかどうかを指定します。  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 トランザクションの分離レベルを指定します。  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 トランザクションを完了しなければならない期間。  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 現在の同期コンテキストを使用してスレッドの実行を選択するかどうかを指定します。  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
