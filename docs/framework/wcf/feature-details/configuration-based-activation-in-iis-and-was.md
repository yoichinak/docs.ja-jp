---
title: IIS と WAS における構成ベースのアクティブ化
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: da98d237c066b70398d3238a75500e8a3abbe887
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857546"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>IIS と WAS における構成ベースのアクティブ化

通常インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) での Windows Communication Foundation (WCF) サービスをホストする場合は、.svc ファイルを提供する必要があります。 .svc ファイルには、サービスの名前と、オプションのカスタム サービス ホスト ファクトリが含まれています。 この追加ファイルによって、管理のオーバーヘッドが増加します。 構成ベースのアクティブ化機能により、.svc ファイルを用意する必要がなくなり、関連するオーバーヘッドも発生しません。

## <a name="configuration-based-activation"></a>構成ベースのアクティブ化

構成ベースのアクティブ化では、以前は .svc ファイルに配置されていたメタデータを受け取り、それを Web.config ファイルに配置します。 内で、<`serviceHostingEnvironment`> 要素がないが、<`serviceActivations`> 要素。 内で、<`serviceActivations`> 要素が 1 つまたは複数 <`add`> 要素、各ホステッド サービスに 1 つ。 <`add`> 要素には場合、サービスおよびサービスの種類、サービス ホスト ファクトリの相対アドレスを設定できる属性が含まれています。 次の構成コード例は、このセクションの使用方法を示しています。

> [!NOTE]
>  各 <`add`> 要素は、サービスまたはファクトリ属性を指定する必要があります。 サービスとファクトリ属性の両方を指定することもできます。

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 このコードを Web.config ファイルに含めると、サービス ソース コードをアプリケーションの App_Code ディレクトリに配置するか、コンパイル済みアセンブリをアプリケーションの Bin ディレクトリに配置することができます。

> [!NOTE]
> - 構成ベースのアクティブ化機能を使用する場合、.svc ファイルのインライン コードはサポートされません。
> - `relativeAddress`属性をなどの相対アドレスに設定する必要があります"\<サブディレクトリ >/service.svc"または"~/\<directory サブ/service.svc"。
> - WCF と関連付けられている既知の拡張子を持たない相対アドレスを登録すると、構成例外がスローされます。
> - 指定された相対アドレスは、仮想アプリケーションのルートが基準になります。
> - 構成の階層的モデルにより、コンピューター レベルおよびサイト レベルの登録された相対アドレスは、仮想アプリケーションによって継承されます。
> - 構成ファイル内での登録は、.svc、.xamlx、.xoml、またはその他のファイルでの設定よりも優先されます。
> - IIS/WAS に送信された URI 内の \ (円記号) は、自動的に / (スラッシュ) に変換されます。 \ を含む相対アドレスが追加され、その相対アドレスを使用する URI を IIS に送信した場合は、円記号がスラッシュに変換されるため、IIS では、それを相対アドレスと一致させることができません。 IIS は、一致するものが見つからなかったことを示すトレース情報を送信します。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)
- [ワークフロー サービスのホストの概要](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [AppFabric のホスティング機能](https://go.microsoft.com/fwlink/?LinkId=201276)