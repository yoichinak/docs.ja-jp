---
title: '方法: 企業内のエンドポイントをロックダウンします。'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 5392db25c0e3ae0051a892831dd013063389d863
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663080"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>方法: 企業内のエンドポイントをロックダウンします。
大規模な企業では、多くの場合、企業のセキュリティ ポリシーに準拠してアプリケーションを開発する必要があります。 次のトピックでは、開発し、コンピューターにインストールされているすべての Windows Communication Foundation (WCF) クライアント アプリケーションの検証に使用できるクライアント エンドポイント検証コントロールをインストールする方法について説明します。  
  
 このエンドポイントの動作がクライアントに追加されるために、検証コントロールがクライアント検証コントロールはここでは、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) machine.config ファイルのセクション。 WCF では、クライアント アプリケーションに対してのみ、共通のエンドポイント動作を読み込みし、サービス アプリケーションだけで一般的なサービスの動作を読み込みます。 サービス アプリケーション用のこの同じ検証コントロールをインストールするには、検証コントロールがサービス動作であることが必要です。 詳細については、次を参照してください。、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)セクション。  
  
> [!IMPORTANT]
>  マークされていないサービスまたはエンドポイントの動作、<xref:System.Security.AllowPartiallyTrustedCallersAttribute>属性 (APTCA) に追加される、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)アプリケーションが部分信頼で実行すると、構成ファイルのセクションでは実行されませんこれが発生すると、環境、および例外がスローされます。 検証コントロールなどの共通動作を強制的に実行するには、次のいずれかを行う必要があります。  
>   
>  -- 共通動作を <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークし、部分信頼アプリケーションとして展開したときに実行できるようにします。 APTCA でマークされたアセンブリを実行できないように、コンピューターでレジストリ エントリを設定できます。  
>   
>  -- アプリケーションが完全信頼アプリケーションとして配置されている場合に、ユーザーが部分信頼環境でアプリケーションを実行するようにコード アクセス セキュリティ設定を変更できないことを確認します。 ユーザーがこのような変更を行うことができる場合、カスタム検証コントロールは実行されず、例外もスローされません。 これを確認する方法の 1 つ、、`levelfinal`オプションを使用して[コード アクセス セキュリティ ポリシー ツール (Caspol.exe)](https://go.microsoft.com/fwlink/?LinkId=248222)を参照してください。  
>   
>  詳細については、[部分的な信頼のベスト プラクティス](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)と[Supported Deployment Scenarios](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)を参照してください。  
  
### <a name="to-create-the-endpoint-validator"></a>エンドポイント検証コントロールを作成するには  
  
1.  <xref:System.ServiceModel.Description.IEndpointBehavior> メソッドに、必要な検証手順を備えた <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> を作成します。 次にコード例を示します。 (、`InternetClientValidatorBehavior`から取得されますが、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプル)。  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  手順 1. で作成したエンドポイント検証コントロールを登録する新しい <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を作成します。 このコード例を次に示します。 (この例の元のコードは、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプル)。  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  コンパイル済みのアセンブリが厳密な名前で署名されていることを確認します。 詳細については、、[厳密名ツール (SN を参照してください。EXE)](https://go.microsoft.com/fwlink/?LinkId=248217)と言語のコンパイラ コマンド。  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>検証コントロールをターゲット コンピューターにインストールするには  
  
1.  適切な機構を使用してエンドポイント検証をインストールします。 企業では、グループ ポリシーと Systems Management Server (SMS) を使用してインストールします。  
  
2.  厳密な名前付きアセンブリを使用してグローバル アセンブリ キャッシュにインストール、 [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md)します。  
  
3.  <xref:System.Configuration?displayProperty=nameWithType> 名前空間の型を使用して、次の処理を行います。  
  
    1.  拡張を追加、 [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)セクションの完全修飾型名を使用して、要素をロックします。  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  動作要素を追加、`EndpointBehaviors`のプロパティ、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)セクションし、要素をロックします。 (サービスの検証コントロールをインストールするには、検証コントロールが <xref:System.ServiceModel.Description.IServiceBehavior> であることが必要です。また、検証コントロールを `ServiceBehaviors` プロパティに追加する必要があります)。次のコード例は、手順 a. と b. の後の適切な構成を示しています。厳密な名前が存在しない点だけが異なります。  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  machine.config ファイルを保存します。 次のコード例では、手順 3. にあるすべてのタスクを実行しますが、変更された machine.config ファイルのコピーはローカルに保存されます。  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>例  
 次のコード例では、machine.config ファイルに共通の動作を追加し、そのコピーをディスクに保存する方法を示します。 `InternetClientValidatorBehavior`から取得されますが、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプル。  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 また、構成ファイルの要素を暗号化する必要がある場合もあります。 詳細については、「参照」を参照してください。  
  
## <a name="see-also"></a>関連項目
- [DPAPI を使用して構成ファイルの要素の暗号化](https://go.microsoft.com/fwlink/?LinkId=94954)
- [RSA を使用して構成ファイルの要素の暗号化](https://go.microsoft.com/fwlink/?LinkId=94955)
