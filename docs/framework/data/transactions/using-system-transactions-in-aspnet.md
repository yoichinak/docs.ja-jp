---
title: ASP.NET での System.Transactions の使用
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: df9a9f1878b2268d1d6bc3d9b05d0ad8d7bcc3f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134589"
---
# <a name="using-systemtransactions-in-aspnet"></a>ASP.NET での System.Transactions の使用
ここでは、 <xref:System.Transactions> アプリケーション内で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を正しく使用する方法について説明します。  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>ASP.NET での DistributedTransactionPermission の有効化  
 <xref:System.Transactions> 部分的に信頼された呼び出し元をサポートしでマークされた、 **AllowPartiallyTrustedCallers**属性 (APTCA)。 <xref:System.Transactions> の信頼レベルは、 <xref:System.Transactions> が公開するリソースの種類 (システム メモリ、共有プロセス全体のリソース、システム全体のリソース、その他のリソースなど)、およびそれらのリソースにアクセスするのに必要な信頼レベルに基づいて定義されます。 部分的に信頼された環境では、 <xref:System.Transactions.DistributedTransactionPermission>が付与されていない限り、完全に信頼されていないアセンブリは、アプリケーション ドメイン内でのみトランザクションを使用できます (この場合、保護されている唯一のリソースはシステム メモリです)。  
  
 <xref:System.Transactions.DistributedTransactionPermission> Microsoft 分散トランザクション コーディネーター (MSDTC) によって管理するトランザクションの管理がエスカレートされるたびに要求されます。 この種のシナリオでは、プロセス全体のリソースと特にグローバルなリソースを使用します。グローバルなリソースは、MSDTC ログで予約されたスペースです。 この使用方法の例として、データベース、または供給するサービスの一部としてデータベースを使用するアプリケーションへの Web フロントエンドがあります。  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] は、独自の信頼レベル セットを持ち、ポリシー ファイルを介して特定のアクセス許可セットを、これらの信頼レベルに関連付けます。 詳細については、次を参照してください。 [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))します。 Windows SDK を最初にインストールした時点では、既定の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ポリシー ファイルは <xref:System.Transactions.DistributedTransactionPermission>に関連付けられていません。 そのため、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションのトランザクションが MSDTC によって管理されるようにエスカレートされると、 <xref:System.Security.SecurityException> を要求した時点で、 <xref:System.Transactions.DistributedTransactionPermission>によりエスカレーションが失敗します。 部分的に信頼された [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の環境でトランザクションのエスカレーションを有効にするには、 <xref:System.Transactions.DistributedTransactionPermission> と同じ既定の信頼レベルで、 <xref:System.Data.SqlClient.SqlClientPermission>を付与する必要があります。 これをサポートする独自のカスタム信頼レベルとポリシー ファイルを構成するか、既定のポリシー ファイルである **Web_hightrust.config** および **Web_mediumtrust.config**を変更できます。  
  
 ポリシー ファイルを変更するには追加、 **SecurityClass**要素**DistributedTransactionPermission**を**SecurityClasses**の下の要素、 **PolicyLevel**要素と、対応する追加**IPermission**の下の要素、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** system.transactions します。 次の構成ファイルに、この例を示します。  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 詳細については[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]、セキュリティ ポリシーを参照してください[securityPolicy 要素 (ASP.NET 設定スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))します。  
  
## <a name="dynamic-compilation"></a>動的コンパイル  
 アクセス時に動的にコンパイルされる <xref:System.Transactions> アプリケーションで [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] をインポートして使用する場合、構成ファイルに <xref:System.Transactions> アセンブリへの参照を配置する必要があります。 具体的には、既定のルートの **Web.config**/**compilation** / **assemblies** セクションに、この参照を追加する必要があります。 次に例を示します。  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 詳細については、次を参照してください。 [(ASP.NET 設定スキーマ) compilation の assemblies の add 要素](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100))します。  
  
## <a name="see-also"></a>関連項目

- [ASP.NET の信頼レベルとポリシー ファイル](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy 要素 (ASP.NET 設定スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [トランザクション管理のエスカレーション](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
