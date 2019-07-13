---
title: ServiceHostFactory を使用したホストの拡張
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991316"
---
# <a name="extending-hosting-using-servicehostfactory"></a>ServiceHostFactory を使用したホストの拡張
標準<xref:System.ServiceModel.ServiceHost>Windows Communication Foundation (WCF) サービスをホストするための API は、WCF のアーキテクチャの機能拡張ポイント。 ユーザーは、この <xref:System.ServiceModel.ServiceHost> の派生型として独自のホスト クラスを定義できます。通常は、<xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> を使用するために <xref:System.ServiceModel.Description.ServiceDescription> をオーバーライドして、これにより、サービスを開く前に、強制的に既定のエンドポイントを追加したり、動作を変更することができます。  
  
 自己ホスト環境では、カスタムの <xref:System.ServiceModel.ServiceHost> を作成する必要はありません。ホストをインスタンス化し、インスタンス化の後で <xref:System.ServiceModel.ICommunicationObject.Open> を呼び出すコードを記述するので、 この 2 つのステップの間に任意の処理を記述できます。 たとえば、新しい <xref:System.ServiceModel.Description.IServiceBehavior> を次のように追加できます。  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 この方法は再利用できません。 説明を操作するコードはホスト プログラム (この場合は Main() 関数) に記述されているので、このロジックを別のコンテキストで使用するのは困難です。 このような強制コードを記述することなく、<xref:System.ServiceModel.Description.IServiceBehavior> を追加する方法もあります。 <xref:System.ServiceModel.ServiceBehaviorAttribute> から派生した属性をサービス実装型に組み込む方法や、カスタム動作の詳細を構成できるようにしておき、構成を使用して動的に組み込む方法が考えられます。  
  
 ただし、サンプル コードを少し修正して問題を解決することもできます。 1 つの方法として、ServiceBehavior を追加するコードを `Main()` 内に記述する代わりに、<xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> から派生した <xref:System.ServiceModel.ServiceHost> メソッドに記述することができます。  
  
```  
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 `Main()` 内には、次のように記述できます。  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 このようにカスタム ロジックをカプセル化、抽象化すると、さまざまなホスト アプリケーションで再利用できます。  
  
 カスタムの <xref:System.ServiceModel.ServiceHost> を Internet Information Services (IIS) や Windows Process Activation Service (WAS) で使用する方法は、それほど単純ではありません。 アプリケーションの代わりにホスティング環境が <xref:System.ServiceModel.ServiceHost> をインスタンス化するという点で、これらの環境は、自己ホスト環境と異なっています。 IIS および WAS ホスティング インフラストラクチャは、<xref:System.ServiceModel.ServiceHost> のカスタム派生物については何も認識しません。  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> は、独自に定義した <xref:System.ServiceModel.ServiceHost> の派生クラスに、IIS または WAS からアクセスする手段として設計されました。 <xref:System.ServiceModel.ServiceHost> から派生したカスタム ホストは、動的に構成され、種類もさまざまであるため、ホスト環境でこれを直接インスタンス化することはありません。 代わりに、WCF はファクトリ パターンを使用して、ホスティング環境とサービスの具象型の間の間接レイヤーを提供します。 特に指定しなければ、<xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す、<xref:System.ServiceModel.ServiceHost> の既定の実装が使用されます。 ファクトリの実装の CLR 型名を指定することで、派生ホストを返す独自のファクトリを提供することもできますが、@ServiceHostディレクティブ。  
  
 基本的なケースでは、独自のファクトリは容易に実装できます。 派生 <xref:System.ServiceModel.Activation.ServiceHostFactory> を返す、カスタムの <xref:System.ServiceModel.ServiceHost> の例を次に示します。  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 既定のファクトリではなくこのファクトリを使用するには、型名を指定、@ServiceHostディレクティブを次のとおりです。  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <xref:System.ServiceModel.ServiceHost> から返す <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A> で行う処理について、技術的には制限はありませんが、ファクトリ実装はできるだけ単純にしておくことをお勧めします。 カスタム ロジックが多い場合は、ファクトリ内ではなくホスト側に記述するようにして、ファクトリは再利用できるようにしておきます。  
  
 ここで、ホスティング API にはもう 1 つのレイヤーがあることを知っておく必要があります。 WCF には、また<xref:System.ServiceModel.ServiceHostBase>と<xref:System.ServiceModel.Activation.ServiceHostFactoryBase>、元の<xref:System.ServiceModel.ServiceHost>と<xref:System.ServiceModel.Activation.ServiceHostFactory>それぞれ派生します。 これらは、メタデータ システムの大部分がカスタム コードに置き換わるような、高度なシナリオを想定して用意されています。
