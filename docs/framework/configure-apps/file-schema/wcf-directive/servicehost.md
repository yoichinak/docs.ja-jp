---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3102ae8d8c28be43883eeaff6c4f829b355384a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111398"
---
# <a name="servicehost"></a>\@ServiceHost
サービス ホストの生成に使用されるファクトリを、ホストされるサービスと、.svc ファイルで提供されるホスティング コードのアクセスとコンパイルに必要なその他のプログラミング部分に関連付けます。  
  
## <a name="syntax"></a>構文  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>属性  
  
#### <a name="service"></a>サービス  
 ホストされるサービスの CLR 型名。 これは、1 つ以上のサービス コンタクトを実装する型の修飾名にする必要があります。  
  
#### <a name="factory"></a>ファクトリ  
 サービス ホストのインスタンス化に使用されるサービス ホスト ファクトリの CLR 型名。 この属性は省略できます。 未指定の場合は、<xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す既定の <xref:System.ServiceModel.ServiceHost> が使用されます。  
  
#### <a name="debug"></a>デバッグ  
 デバッグ シンボルを使用した Windows Communication Foundation (WCF) サービスをコンパイルする必要があるかどうかを示します。 `true` 場合は、WCF サービスは、デバッグ シンボルでコンパイルする必要があります。それ以外の場合、`false`します。  
  
#### <a name="language"></a>言語  
 ファイル (.svc) 内のすべてのインライン コードをコンパイルするときに使用する言語を指定します。 値は、C#、VB、JS (それぞれ、C#、Visual Basic .NET、および JScript .NET を示す) など、.NET がサポートする任意の言語を表します。 この属性は省略できます。  
  
#### <a name="codebehind"></a>CodeBehind  
 XML Web サービスを実装するクラスが同じファイル内に存在せず、アセンブリとしてコンパイルされずに \Bin ディレクトリに置かれているとき、XML Web サービスを実装するソース ファイルを指定します。  
  
## <a name="remarks"></a>Remarks  
 <xref:System.ServiceModel.ServiceHost>サービスをホストするために使用、Windows Communication Foundation (WCF) のプログラミング モデル内の拡張ポイントです。 ファクトリ パターンは、ホスティング環境が直接インスタンス化できないポリモーフィック型の可能性があるため、<xref:System.ServiceModel.ServiceHost> のインスタンス化に使用されます。  
  
 既定の実装では <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。 ファクトリの実装の CLR 型名を指定することで、独自のファクトリ (派生ホストを返す) を行うことができますが、 [ \@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ。  
  
 既定のファクトリではなく独自のカスタム サービス ホスト ファクトリに使用してでの型名を指定した、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブを次のとおりです。  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 ファクトリ実装はできるだけ軽量に保持してください。 多くのカスタム ロジックがある場合は、それらのロジックをファクトリ内部ではなくホスト内部に置くとコードがさらに再利用可能になります。  
  
 たとえば、AJAX 対応のエンドポイントを有効にする`MyService`、指定、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>の値を`Factory`属性に、既定ではなく、<xref:System.ServiceModel.Activation.ServiceHostFactory>で、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)としてディレクティブ次の例に示します。  
  
## <a name="example"></a>例  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>関連項目

- [カスタム サービス ホスト](../../../../../docs/framework/wcf/samples/custom-service-host.md)
