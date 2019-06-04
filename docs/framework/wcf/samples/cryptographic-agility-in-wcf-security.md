---
title: WCF セキュリティ暗号化方式の指定
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: b8e3b6dc62baf31901520d7f5edac0529e937016
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490942"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF セキュリティ暗号化方式の指定

このサンプルでは、Windows Communication Foundation (WCF) クライアントとサービスで迅速な暗号化の実装を提供する標準またはカスタム アルゴリズムで指定する方法を示します。 サンプルは、以下のプロジェクトで構成されます。

**サービス**

これは、自己ホスト型 WCF サービスを実装する、`ICalculator`インターフェイスを使用してエンドポイントをセキュリティで保護、<xref:System.ServiceModel.WSHttpBinding>セキュリティで保護されたセッションと信頼できるセッションは無効にします。 このサービスは、カスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。

**クライアント**

これは、認証成功後に、サービスにアクセスする WCF クライアントです。 このクライアントは、`ICalculator` インターフェイスによって公開され、サービスによって実装される操作を呼び出します。 このクライアントも、同じカスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。

## <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2012 で CryptoAgility.sln ソリューションを開きます。

2. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。

3. ファイル エクスプ ローラーを開き、\WCF\Basic\Security\CryptoAgility\Service\bin ディレクトリに移動し、service.exe を右クリックして、service.exe ファイルを管理者特権で実行**管理者として実行**します。

4. \WCF\Basic\Security\CryptoAgility\Client\bin ディレクトリに移動して、client.exe ファイルを通常の方法で実行します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>関連項目

- [Windows Communication Foundation セキュリティ](../feature-details/security.md)
