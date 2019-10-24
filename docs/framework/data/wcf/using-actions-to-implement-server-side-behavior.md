---
title: アクションを使用してサーバー側の動作を実装する
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 7068845054e04a002296e7c157655eef6a98db78
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774138"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>アクションを使用してサーバー側の動作を実装する

OData アクションを使用すると、OData サービスから取得したリソースに対する動作を実装できます。 たとえば、リソースとしてデジタル ムービーについて考えてみましょう。デジタル ムービーについては、チェックアウト、評価やコメント、チェックインなど、多様な操作が考えられます。 これらはすべて、デジタル ムービーを管理するために WCF Data Services で実装できるアクションの例です。 アクションは、そのアクションを呼び出すことのできる対象のリソースが含まれている OData 応答に記述します。 ユーザーが、デジタル ムービーを表すリソースを要求した場合、WCF Data Services から返される応答には、そのリソースに使用できるアクションに関する情報が含まれています。 アクションを使用できるかどうかは、データ サービスまたはリソースの状態によって変わる場合があります。 たとえば、デジタル ムービーがチェックアウトされている場合、それを別のユーザーがチェックアウトすることはできません。 クライアントは、URL を指定するだけでアクションを呼び出すことができます。 たとえば、`http://MyServer/MovieService.svc/Movies(6)` は特定のデジタルムービーを識別し、`http://MyServer/MovieService.svc/Movies(6)/Checkout` は特定のムービーに対してアクションを呼び出します。 アクションを使用すると、データ モデルを公開することなくサービス モデルを公開することができます。 先ほどのムービー サービスを例とすると、評価データをリソースとして直接公開せずにムービーをユーザーが評価できるようにするというケースが考えられます。 そこで、たとえば Rate (評価) アクションを実装することにより、リソースとして評価データに直接アクセスせずに、ムービーをユーザーが評価できるようにすることができます。

## <a name="implementing-an-action"></a>アクションの実装
 サービスアクションを実装するには、<xref:System.IServiceProvider>、[ず](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))、および[IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103))インターフェイスを実装する必要があります。 <xref:System.IServiceProvider> により、WCF Data Services は[ず](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))の実装を取得できます。 [ず](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))では、サービスアクションの作成、検索、記述、および呼び出しを WCF Data Services できます。 [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103))を使用すると、サービスアクションの動作を実装するコードを呼び出し、結果を取得できます (存在する場合)。 WCF Data Services は呼び出しごとの WCF サービスであり、サービスの新しいインスタンスは、サービスが呼び出されるごとに作成されます。  サービスの作成時に、不要な作業が行われないよう注意してください。

### <a name="iserviceprovider"></a>IServiceProvider
 <xref:System.IServiceProvider> には、<xref:System.IServiceProvider.GetService%2A> というメソッドが含まれています。 このメソッドは、メタデータ サービス プロバイダーやデータ サービス アクション プロバイダーなど、いくつかのサービス プロバイダーを取得するために、WCF Data Services によって呼び出されます。 データサービスアクションプロバイダーの確認を求められたら、[ず](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))の実装を返します。

### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider
 [ず](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))には、使用可能なアクションに関する情報を取得できるようにするメソッドが含まれています。 [ず](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))を実装する場合は、サービスの[ず](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))の実装によって定義されるサービスのメタデータを、アクションを使用して、それらのアクションへのディスパッチを処理することによって、対応.

#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction
 [AdvertiseServiceAction メソッド](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103))は、指定されたリソースで使用可能なアクションを判別するために呼び出されます。 このメソッドは、常時使用可能ではないアクションについてのみ呼び出されます。 このメソッドの用途は、要求されているリソースの状態またはサービスの状態に基づいて、アクションを OData 応答に含めるかどうかを確認することです。 この確認をどのように行うかは、開発者が指定する必要があります。 使用可能かどうかを計算する処理の負荷が高く、現在のリソースがフィード内にある場合は、確認をスキップしてアクションの情報提供を行うこともできます。 返される現在のリソースがフィードの一部である場合は、`inFeed` パラメーターが `true` に設定されます。

#### <a name="createinvokable"></a>CreateInvokable
 [Createinvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103))可能なは、アクションの動作を実装するコードをカプセル化するデリゲートを含む[IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103))を作成するために呼び出されます。 これにより、 [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103))インスタンスが作成されますが、アクションは呼び出されません。 WCF Data Services のアクションは副作用を伴うため、更新プロバイダーと連携して、その変更をディスクに保存する必要があります。 更新プロバイダーの SaveChanges () メソッドが呼び出され、 [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103))メソッドが呼び出されます。

#### <a name="getserviceactions"></a>GetServiceActions
 このメソッドは、WCF データサービスが公開するすべてのアクションを表す[Serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))インスタンスのコレクションを返します。 [Serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))は、アクションのメタデータ表現であり、アクション名、パラメーター、戻り値の型などの情報が含まれています。

#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType
 このメソッドは、指定されたバインディングパラメーターの型にバインドできるすべての[Serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))インスタンスのコレクションを返します。 つまり、指定されたリソースの種類 (バインディングパラメーターの型とも呼ばれます) に対して動作できるすべての[Serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))。これは、サービスがリソースを返すときに、そのリソースに対して呼び出すことができるアクションに関する情報を含めるために使用されます。 このメソッドが返すアクションは、(派生型ではなく) 指定どおりのバインディング パラメーターの種類にバインドできるアクションのみです。 このメソッドは、要求ごと、検出された種類ごとに 1 回呼び出され、結果は WCF Data Services によってキャッシュされます。

#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction
 このメソッドは、指定された[Serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))を検索し、 [serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))が見つかった場合は `true` を返します。 見つかった場合は、`serviceAction` `out` パラメーターに[Serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))が返されます。

### <a name="idataserviceinvokable"></a>IDataServiceInvokable
 このインターフェイスは、WCF Data Services アクションの実行方法を提供します。 IDataServiceInvokable を実装する場合は、次の 3 つを行う必要があります。

1. パラメーターをキャプチャし、場合によってはマーシャリングを行う。

2. Invoke() の呼び出し時に、アクションを実際に実装するコードにパラメーターをディスパッチする。

3. GetResult() を使用して取得できるように、Invoke() の結果を保存する。

 パラメーターは、トークンとして渡すことができます。 これは、リソースを表すトークンを扱うデータ サービス プロバイダーを作成することができるためです。ただしその場合は、実際のアクションにディスパッチする前に、トークンを実際のリソースに変換 (マーシャリング) する必要があります。 パラメーターがマーシャリングされた後は、アクションが呼び出されたときに発生するリソースに対する変更が保存され、ディスクに書き込まれるように、パラメーターを編集可能な状態にする必要があります。

 このインターフェイスには、Invoke および GetResult という 2 つのメソッドが必要です。 Invoke はアクションの動作を実装するデリゲートを呼び出し、GetResult はアクションの結果を返します。

## <a name="invoking-a-wcf-data-service-action"></a>WCF Data Services アクションの呼び出し
 アクションは HTTP POST 要求を使用して呼び出します。 リソースの後にアクション名を続けて URL を指定します。 パラメーターは、要求の本文を使用して渡します。 たとえば、MovieService というサービスがあり、Rate というアクションが公開されているとします。 この場合、特定のムービーに対して Rate アクションを呼び出すには、次のような URL 使用することができます。

 `http://MovieServer/MovieService.svc/Movies(1)/Rate`

 Movies(1) は評価対象のムービーを示し、Rate は Rate アクションを指定しています。 次の例に示すように、評価の実際の値は HTTP 要求の本文に含まれます。

```http
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1
Content-Type: application/json
Content-Length: 20
Host: localhost:15238
{
   "rating": 4
}
```

> [!WARNING]
> 上のサンプル コードが動作するのは、JSON Light をサポートする WCF Data Services 5.2 以降を使用している場合のみです。 それより前のバージョンの WCF Data Services を使用している場合は、Verbose JSON の Content-Type を「`application/json;odata=verbose`」のように指定する必要があります。

 また、次のコード スニペットのように、WCF Data Services クライアントを使用してアクションを呼び出すこともできます。

```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));
//...
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```

 上のコード スニペットの `MoviesModel` クラスは、Visual Studio の [サービス参照の追加] で WCF Data Services への参照を追加することでが生成されたものです。

## <a name="see-also"></a>関連項目

- [WCF Data Services 4.5](index.md)
- [WCF Data Services の定義](defining-wcf-data-services.md)
- [WCF Data Services の開発と配置](developing-and-deploying-wcf-data-services.md)
- [カスタム データ サービス プロバイダー](custom-data-service-providers-wcf-data-services.md)
