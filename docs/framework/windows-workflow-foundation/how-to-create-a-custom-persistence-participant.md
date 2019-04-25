---
title: '方法: カスタム永続参加要素を作成する'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 1de2abb8ababd794cd644733b6e4ab0ed42b1810
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770010"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>方法: カスタム永続参加要素を作成する
次の手順では、永続参加要素を作成します。 参照してください、[永続化に参加している](https://go.microsoft.com/fwlink/?LinkID=177735)サンプルと[ストア拡張](store-extensibility.md)永続参加要素の実装例に関するトピック。  
  
1. <xref:System.Activities.Persistence.PersistenceParticipant> または <xref:System.Activities.Persistence.PersistenceIOParticipant> クラスから派生するクラスを作成します。 PersistenceIOParticipant クラスは、I/O 操作に参加できることに加え、PersistenceParticipant クラスと同じ拡張ポイントを提供します。 次のうち、必要な手順を行います。  
  
2. <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> メソッドを実装します。 **CollectValues**メソッドには、2 つのディクショナリ パラメーター、もう 1 つ (後でクエリで使用)、書き込み専用の値を格納するためおよび読み取り/書き込み値を格納する 1 つ。 このメソッドでは、永続参加要素に固有のデータをこれらのディクショナリに設定する必要があります。 各ディクショナリには、値の名前がキーとして格納されているほか、値そのものが <xref:System.Runtime.DurableInstancing.InstanceValue> オブジェクトとして格納されています。  
  
     ReadWriteValues ディクショナリ内の値としてパッケージ化**InstanceValue**オブジェクト。 書き込み専用のディクショナリ内の値としてパッケージ化**InstanceValue** InstanceValueOptions.Optional および InstanceValueOption.WriteOnly セットでのオブジェクト。 各**InstanceValue**によって提供される、 **CollectValues**すべての永続参加要素の実装は、一意の名前をいる必要があります。  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3. <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドを実装します。 **MapValues**メソッド パラメーターに似ている 2 つのパラメーターを受け取りますが、 **CollectValues**メソッドを受け取ります。 収集されたすべての値、 **CollectValues**ステージはこれらのディクショナリ パラメーターを介して渡されます。 によって追加された新しい値、 **MapValues**ステージは、書き込み専用の値に追加されます。  書き込み専用のディクショナリが、インスタンスの値に直接関連付けられていない外部ソースにデータを提供するために使用されます。 実装によって提供される各値、 **MapValues**メソッドすべての永続参加要素は、一意の名前をいる必要があります。  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドは <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が提供しない機能を提供し、<xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が処理しなかった別の永続参加により提供される、別の値への依存関係が許可されます。  
  
4. 実装、 **PublishValues**メソッド。 **PublishValues**メソッドは、永続化ストアから読み込まれたすべての値を含む辞書を受け取ります。  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5. 実装、 **BeginOnSave**メソッド、参加要素が I/O の永続参加要素の場合。 このメソッドは保存操作中に呼び出されます。 このメソッドでは、I/O に付随する永続化 (ワークフロー インスタンスの保存) を行う必要があります。  ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。  さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6. 実装、 **BeginOnLoad**メソッド、参加要素が I/O の永続参加要素の場合。 このメソッドは読み込み操作中に呼び出されます。 このメソッドでは、I/O に付随するワークフロー インスタンスの読み込みを行う必要があります。 ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。 さらに、I/O の永続化参加要素は、トランザクションの一貫性の要件の 1 つはそれ以外の場合、使用されない場合、ホストの場合のトランザクションを永続化を作成をアドバタイズすることがあります。  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
