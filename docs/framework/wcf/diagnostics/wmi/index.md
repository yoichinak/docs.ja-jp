---
title: 診断用の WMI (Windows Management Instrumentation) の使用
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: ecc5c754a51a8e1a52797dfd0af0891704eaad1f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591238"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>診断用の WMI (Windows Management Instrumentation) の使用
Windows Communication Foundation (WCF) は、WCF Windows Management Instrumentation (WMI) プロバイダーを介して実行時のサービスの検査データを公開します。  
  
## <a name="enabling-wmi"></a>WMI の有効化  
 WMI は、Web ベースのエンタープライズ管理 (WBEM) 標準をマイクロソフトが実装したものです。 WMI SDK の詳細については、次を参照してください。 [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page)します。 WBEM は、アプリケーションが Management Instrumentation を外部管理ツールに開示する業界標準の方法です。  
  
 WMI プロバイダーは、WBEM と互換性のあるインターフェイスを通して実行時にインストルメンテーションを公開するコンポーネントです。 これは、属性と値のペアを持つ WMI オブジェクトのセットで構成されます。 ペアには多くの単純型を指定できます。 管理ツールは、実行時にインターフェイスを介してサービスに接続できます。 WCF では、アドレス、バインディング、動作、およびリスナーなどのサービスの属性を公開します。  
  
 組み込みの WMI プロバイダーは、アプリケーションの構成ファイルでアクティブにできます。 これを行う、`wmiProviderEnabled`の属性、 [\<診断 >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)で、 [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)セクションで、次の例に示すように構成します。  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 この構成エントリには、WMI インターフェイスが開示されます。 管理アプリケーションはこのインターフェイスを通して接続し、アプリケーションの Management Instrumentation にアクセスできるようになります。  
  
## <a name="accessing-wmi-data"></a>WMI データへのアクセス  
 WMI データには、複数の異なる方法でアクセスできます。 Microsoft Visual Basic アプリケーション、スクリプトは、WMI Api を提供するC++アプリケーション、および .NET Framework です。 詳細については、次を参照してください。 [WMI を使用した](https://go.microsoft.com/fwlink/?LinkId=95183)します。  
  
> [!CAUTION]
>  .NET Framework 提供のメソッドを使用し、プログラムで WMI データにアクセスする場合、そのようなメソッドは接続確立時に例外をスローする場合があることを認識しておく必要があります。 接続は、<xref:System.Management.ManagementObject> インスタンスの構築中に確立されませんが、実際のデータ交換が含まれた最初の要求時に確立されます。 したがって、`try..catch` ブロックを使用して例外をキャッチする必要があります。  
  
 トレース レベルやメッセージ ログ レベルだけでなく、WMI の `System.ServiceModel` トレース ソースのメッセージ ログ オプションも変更できます。 これを行うへのアクセス、 [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)インスタンスで、これらのブール型プロパティを公開します: `LogMessagesAtServiceLevel`、 `LogMessagesAtTransportLevel`、 `LogMalformedMessages`、および`TraceLevel`します。 そのため、メッセージ ログ用のトレース リスナーを構成していても、これらのオプションを構成で `false` に設定している場合は、後でアプリケーションを実行しているときに `true` に変更できます。 これで、メッセージ ログが実行時に有効になります。 同様に、構成ファイルでメッセージ ログを有効にしている場合は、実行時に WMI を使用して無効にできます。  
  
 構成ファイルで、メッセージ ログのメッセージ ログ トレース リスナーまたはトレースの `System.ServiceModel` トレース リスナーが指定されていない場合、WMI が変更を受け入れても変更は有効になりません。 各リスナーを正しく設定の詳細については、次を参照してください。[メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)と[トレースの構成](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)します。 構成で設定された他のすべてのトレース ソースのトレース レベルは、アプリケーションが開始されると有効になり変更できません。  
  
 WCF の公開、`GetOperationCounterInstanceName`スクリプト メソッド。 このメソッドに操作名を指定した場合、このメソッドはパフォーマンス カウンターのインスタンス名を返します。 ただし、このメソッドは入力を検証しません。 したがって、正しくない操作名を指定した場合、正しくないカウンター名が返されます。  
  
 `OutgoingChannel`のプロパティ、`Service`インスタンス内で目的のサービスに WCF クライアントが作成されていない場合は、別のサービスに接続するためのサービスによって開かれたチャネルをカウントしません、`Service`メソッド。  
  
 **注意**WMI のみをサポート、<xref:System.TimeSpan>最大 3 つの 10 進数のポイントの値します。 たとえば、サービスでプロパティの 1 つを <xref:System.TimeSpan.MaxValue> に設定した場合、WMI ではその値を小数点以下 3 桁より下を切り捨て表示します。  
  
## <a name="security"></a>セキュリティ  
 WCF WMI プロバイダーでは、環境でサービスの検出ができる、のでへのアクセスを許可するための十分な注意を実行する必要があります。 既定の "管理者のみ" のアクセスを緩めた場合、信頼性の低いパーティに環境内の機密性のあるデータへのアクセスを許可する場合があります。 特にリモート WMI アクセスに対するアクセス許可を緩めた場合、大量の攻撃を受ける可能性があります。 過剰の WMI 要求により大量の処理が発生した場合、パフォーマンスが低下する可能性があります。  
  
 さらに、MOF ファイルに対するアクセス許可を緩めた場合、信頼性の低いパーティが WMI の動作を操作して WMI スキーマに読み込まれるオブジェクトを変更することができます。 たとえば、フィールドを削除して、重要データを管理者から隠したり、例外を設定しないかまたは例外の原因とならないフィールドを追加したりすることができます。  
  
 既定では、WCF WMI プロバイダー execute が付与されます"メソッド"、「プロバイダーによる書き込み」、および「アカウントの有効化」権限が管理者、および ASP.NET、Local Service、およびネットワーク サービスの「アカウントの有効化」権限。 特に、[!INCLUDE[wv](../../../../../includes/wv-md.md)] 以外のプラットフォームでは、ASP.NET アカウントは WMI ServiceModel 名前空間に対して読み取りアクセスが可能です。 特定のユーザー グループに対してこれらの権限を付与したくない場合は、WMI プロバイダーを非アクティブにするか (既定では無効に設定されています)、特定のユーザー グループのアクセスを無効にする必要があります。  
  
 また、構成を使用して WMI を有効にする場合、ユーザー権限が不十分のため WMI が有効にならない場合があります。 ただし、このエラーを記録するイベントはイベント ログに書き込まれません。  
  
 ユーザー権限のレベルを変更するには、次の手順に従います。  
  
1. [開始] をクリックしておよび実行し、入力**compmgmt.msc**します。  
  
2. 右クリックして**サービスとアプリケーション WMI コントロール**を選択する**プロパティ**します。  
  
3. 選択、**セキュリティ** タブに移動し、 **Root/servicemodel**名前空間。 をクリックして、**セキュリティ**ボタンをクリックします。  
  
4. 特定のグループまたはアクセスを制御し、使用するユーザーを選択、**許可**または**Deny**アクセス許可を構成するチェック ボックスをオンします。  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>追加ユーザーへの WCF WMI 登録権限の付与  
 WCF は管理データを WMI に公開します。 これには、「分離プロバイダー」とも呼ばれる、インプロセス WMI プロバイダーをホストします。 管理データを公開するには、このプロバイダーを登録するアカウントに適切な権限が必要です。 Windows では、権限を持つアカウントの少数のセットのみが、既定で分離プロバイダーを登録できます。 ユーザーは通常、既定のセットではないアカウントで実行している WCF サービスから WMI データを公開するので、これは問題です。  
  
 このアクセスを提供するために、管理者は、次の権限を追加のアカウントに次の順序で付与する必要があります。  
  
1. WCF WMI 名前空間へのアクセス権限  
  
2. WCF 分離 WMI プロバイダーの登録権限  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>WMI 名前空間へのアクセス権限を付与するには  
  
1. 次の PowerShell スクリプトを実行します。  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     この PowerShell スクリプトでは、組み込みのユーザー グループで、"root/servicemodel"WMI 名前空間へのアクセスを付与するのにセキュリティ記述子定義言語 (SDDL) を使用します。 次の ACL が指定されます。  
  
    - 組み込みの管理者 (BA) – 既にアクセス権を持っています。  
  
    - ネットワーク サービス (NS) - 既にアクセス権を持っています。  
  
    - ローカル システム (LS) - 既にアクセス権を持っています。  
  
    - 組み込みのユーザー – アクセス権を付与するグループ。  
  
#### <a name="to-grant-provider-registration-access"></a>プロバイダーに登録アクセス権を付与するには  
  
1. 次の PowerShell スクリプトを実行します。  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>任意のユーザーまたはグループへのアクセス権の付与  
 このセクションの例では、すべてのローカル ユーザーに WMI プロバイダー登録権限を付与します。 組み込まれていないユーザーまたはグループにアクセス権を付与する場合は、そのユーザーまたはグループのセキュリティ識別子 (SID) を取得する必要があります。 任意のユーザーの SID を取得する簡単な方法はありません。 1 つの方法としては、目的のユーザーとしてログオンし、次のシェル コマンドを発行します。  
  
```  
Whoami /user  
```  
  
 これにより、現在のユーザーの SID が提供されますが、この方法を使用して任意のユーザーで SID を取得することはできません。 SID を取得するもう 1 つのメソッドは、使用する、 [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467)ツールから、[管理タスク用の Windows 2000 リソース キット ツール](https://go.microsoft.com/fwlink/?LinkId=178660)します。 このツールは、2 人のユーザー (ローカルまたはドメイン) の SID を比較し、副作用として、2 つの SID をコマンド ラインに出力します。 詳細については、次を参照してください。 [Well Known Sid](https://go.microsoft.com/fwlink/?LinkId=186468)します。  
  
## <a name="accessing-remote-wmi-object-instances"></a>リモート WMI オブジェクトのインスタンスへのアクセス  
 リモート コンピューター上の WCF WMI インスタンスにアクセスする必要がある場合は、パケットのプライバシーへのアクセスに使用するツールを有効にする必要があります。 次のセクションでは、WMI CIM Studio、Windows Management Instrumentation テスト、および .NET SDK 2.0 を使用してこれらを実現する方法を説明します。  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 インストールした場合[WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185)、WMI インスタンスのアクセスに、WMI CIM Studio を使用することができます。 このツールは次のフォルダーにあります。  
  
 **%windir%\Program Files\WMI Tools\\**  
  
1. **名前空間への接続:** ウィンドウで、「 **「root \servicemodel」**  をクリック**ok をクリックします。**  
  
2. **WMI CIM Studio Login**ウィンドウで、をクリックして、**オプション >>** ボタン ウィンドウを展開します。 選択**パケットのプライバシー**の**認証レベル**、 をクリック**OK**します。  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Management Instrumentation テスト  
 このツールは Windows によりインストールされます。 これを実行するには、」と入力してコマンド コンソールを起動**cmd.exe**で、**開始/実行** ダイアログ ボックスをクリックします**OK**します。 次に、入力**wbemtest.exe**コマンド ウィンドウにします。 Windows Management Instrumentation テスト ツールが起動します。  
  
1. をクリックして、 **Connect**ウィンドウの右上隅のボタンをクリックします。  
  
2. 新しいウィンドウで次のように入力します。 **「root \servicemodel」** の、 **Namespace**フィールド、および選択**パケットのプライバシー**の**認証レベル**します。 **[接続]** をクリックします。  
  
### <a name="using-managed-code"></a>マネージド コードの使用  
 <xref:System.Management> 名前空間が提供するクラスを使用して、リモートの WMI インスタンスにプログラムでアクセスすることもできます。 これを実行する方法を次のコード例に示します。  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
