---
title: ASP.NET 互換性
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 01329769b74c8a5841b5a2024d3ed674c108be1c
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487666"
---
# <a name="aspnet-compatibility"></a>ASP.NET 互換性
このサンプルでは、Windows Communication Foundation (WCF) での ASP.NET 互換モードを有効にする方法を示します。 ASP.NET ファイル/URL 承認、セッション状態などの機能の ASP.NET 互換モードは、ASP.NET アプリケーション パイプラインに完全に参加し、ことで実行されているサービスを使用して、<xref:System.Web.HttpContext>クラス。 <xref:System.Web.HttpContext>クラスは、cookie、セッション、およびその他の ASP.NET 機能へのアクセスを使用できます。 このモードでは、バインディングは HTTP トランスポートを使用し、サービス自体は IIS でホストされる必要があります。  
  
 このサンプルでは、クライアントはコンソール アプリケーション (.exe) で、サービスはインターネット インフォメーション サービス (IIS) によってホストされています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
このサンプルを実行するには、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] アプリケーション プールが必要です。 新しいアプリケーション プールの作成または既定のアプリケーション プールの変更を行うには、次の手順に従います。  

1. **[コントロール パネル]** を開きます。  開く、**管理ツール**アプレット、**システムとセキュリティ**見出し。 開く、**インターネット インフォメーション サービス (IIS) マネージャー**アプレットです。  

2. Treeview を展開し、**接続**ウィンドウ。 選択、**アプリケーション プール**ノード。  

3. 使用する既定のアプリケーション プールを設定する[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)](既存のサイトと非互換性の問題が発生する可能性があります、) を右クリックし、 **DefaultAppPool**リスト項目と選択**基本設定しています...** . 設定、 **.Net Framework のバージョン**プルダウンを **.Net Framework v4.0.30128** (またはそれ以降)。  

4. 使用する新しいアプリケーション プールを作成する[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)](互換性を保持する他のアプリケーション)、右クリックし、**アプリケーション プール**ノード**アプリケーション プールの追加しています...** . 新しいアプリケーション プールの名前を指定し、設定、 **.Net Framework のバージョン**プルダウンを **.Net Framework v4.0.30128** (またはそれ以降)。 下、セットアップを実行する手順は、後に右クリックし、 **ServiceModelSamples**アプリケーションと選択**アプリケーションの管理**、**詳細設定しています...** . 設定、**アプリケーション プール**を新しいアプリケーション プール。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)、電卓サービスを実装します。 `ICalculator` コントラクトは、一連の算術演算を実行して実行結果を保持できるように `ICalculatorSession` コントラクトに変更されました。  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 サービスはこの機能を使用して、複数のサービス操作が呼び出されて計算を実行する際に、各クライアントの状態を保持します。 クライアントは `Result` を呼び出して現在の結果を取得したり、`Clear` を呼び出してその結果をクリアし、0 にすることができます。  
  
 サービスは、各クライアント セッションの結果を格納するのに ASP.NET セッションを使用します。 これにより、サービスは、サービスへの複数の呼び出しによる各クライアントの実行結果を保持できます。  
  
> [!NOTE]
> ASP.NET セッション状態と WCF のセッションは、非常に異なるものです。 参照してください[セッション](../../../../docs/framework/wcf/samples/session.md)WCF セッションの詳細について。
  
 サービスが ASP.NET セッション状態で、詳細な依存関係がある、正しく機能する ASP.NET 互換モードが必要です。 これらの要件は、`AspNetCompatibilityRequirements` 属性を適用することにより宣言によって表されます。  
  
```csharp  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行済みであるかどうかを必ず、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. ソリューションがビルドされたら、IIS 7.0 で ServiceModelSamples アプリケーションを設定する Setup.bat を実行します。 ServiceModelSamples ディレクトリは、IIS 7.0 のアプリケーションとして表示されます。  
  
4. 1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
## <a name="see-also"></a>関連項目

- [AppFabric のホストおよび永続化のサンプル](https://go.microsoft.com/fwlink/?LinkId=193961)
