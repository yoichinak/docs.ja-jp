---
title: POCO サポート
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 8d94d6a9700c38014aa53ee9910b53239fc28b0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640031"
---
# <a name="poco-support"></a>POCO サポート
このサンプルでは、マークされていない型 (シリアル化属性が適用されていない型で、POCO (Plain Old CLR Object) 型と呼ばれる場合もあります) のシリアル化のサポートについて説明します。 <xref:System.Runtime.Serialization.DataContractSerializer> では、既定のコンストラクタを持つすべてのマークされていないパブリック型について、データ コントラクトを推測します。 データ コントラクトを使用すると、サービスと構造化データをやり取りできます。 マークされていない種類の詳細については、[シリアル化できる型](../../../../docs/framework/wcf/feature-details/serializable-types.md)を参照してください。  
  
 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)がプリミティブ数値型ではなく複素数を使用します。 またに似ています、[基本的なデータ コントラクト](../../../../docs/framework/wcf/samples/basic-data-contract.md)点を除いて、サンプル、<xref:System.Runtime.Serialization.DataContractAttribute>と<xref:System.Runtime.Serialization.DataMemberAttribute>属性は使用されません。  
  
 サービスはインターネット インフォメーション サービス (IIS) によってホストされています。クライアントはコンソール アプリケーション (.exe) です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 `ComplexNumber` クラスは、`ServiceContract` で使用されます。 次のサンプル コードに示すように、`ComplexNumber` 型には、<xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性がありません。 既定では、パブリック プロパティとパブリック フィールドはすべてシリアル化されます。  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>関連項目
- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [シリアル化可能な型](../../../../docs/framework/wcf/feature-details/serializable-types.md)
