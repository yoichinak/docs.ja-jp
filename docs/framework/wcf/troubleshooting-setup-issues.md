---
title: セットアップに関する問題のトラブルシューティング
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 69242ec745f2a5b945ae64eb558070dbf0d39c10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299619"
---
# <a name="troubleshooting-setup-issues"></a>セットアップに関する問題のトラブルシューティング
このトピックでは、Windows Communication Foundation (WCF) がセットアップ問題のトラブルシューティングを行う方法について説明します。  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>.NET Framework 3.0 の MSI 修復操作の実行では修復されない一部の Windows Communication Foundation レジストリ キー  
 次のいずれかのレジストリ キーを削除した場合  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 起動される .NET Framework 3.0 インストーラーを使用して修復を実行する場合、キーが再作成されません、**プログラムの追加/削除**アプレット**コントロール パネルの**します。 これらのキーを正しく再作成するには、.NET Framework 3.0 をアンインストール後、再インストールする必要があります。  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>WMI サービスの破損により .NET Framework 3.0 パッケージのインストール中に Windows Communication Foundation WMI プロバイダーのインストールがブロックされる  
 WMI サービスの破損により、Windows Communication Foundation WMI プロバイダーのインストールがブロックされることがあります。 インストール中、Windows Communication Foundation インストーラーは mofcomp.exe コンポーネントを使用して WCF .mof ファイルを登録できません。 発生する現象を次に示します。  
  
1. .NET Framework 3.0 のインストールは正常に完了するのに、WCF WMI プロバイダーが登録されない。  
  
2. アプリケーション イベント ログに、WCF の WMI プロバイダーの登録、または mofcomp.exe の実行に関する問題を示すエラー イベントが表示される。  
  
3. ユーザーの %temp% ディレクトリの dd_wcf_retCA* という名前のセットアップ ログ ファイルに、WCF WMI プロバイダーの登録に失敗したことが示される。  
  
4. イベント ログまたはセットアップ トレース ログ ファイルに、次の例外のいずれかが記録される。  
  
     ServiceModelReg [11:09:59:046]:System.ApplicationException:Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     または  
  
     ServiceModelReg [07:19:33:843]:System.TypeInitializationException:'System.management.managementpath' の型の初期化子は、例外をスローしました。 ---> System.Runtime.InteropServices.COMException (0x80040154):次のエラーにより失敗しました。 CLSID {cf4cc405-e2c5-4ddd-b3ce-5e7582d8c9fa} を含むコンポーネントの COM クラス ファクトリを取得します。80040154.  
  
     または  
  
     ServiceModelReg [07:19:32:750]:System.IO.FileNotFoundException:ファイルまたはアセンブリ 'C:\WINDOWS\system32\wbem\mofcomp.exe'、またはその依存関係の 1 つを読み込めませんでした。 指定されたファイルが見つかりません。  
  
     ファイル名:'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 上で説明した問題を解決するためには、次の手順を実行する必要があります。  
  
1. 実行[WMI 診断ユーティリティ、バージョン 2.0](https://go.microsoft.com/fwlink/?LinkId=94685)の WMI サービスを修復します。 詳細については、このツールを使用して、次を参照してください。、 [WMI 診断ユーティリティ](https://go.microsoft.com/fwlink/?LinkId=94686)トピック。  
  
 使用して、.NET Framework 3.0 のインストールを修復、**プログラムの追加/削除**アプレットにある**コントロール パネルの**、または .NET Framework 3.0 をアンインストール/再インストールします。  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>.NET Framework 3.5 のインストール後に .NET Framework 3.0 を修復すると、.NET Framework 3.5 によって導入された machine.config 内の構成要素が削除される  
 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] をインストールした後に .NET Framework 3.0 を修復すると、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] によって導入された machine.config 内の構成要素が削除されます。 ただし、web.config は元の状態のままになります。 回避を修復するには[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]ARP、または使用を使用してその後、[ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)で、`/c`スイッチします。  
  
 [ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ または %windir%\Microsoft.NET\framework64\v3.5\ にあります  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>.NET Framework 3.5 のインストール後に WCF/WF Webhost に対して IIS を適切に構成する  
 ときに[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]のインストールは、追加の WCF に関連する IIS 構成設定を構成できない場合、インストール ログでエラー ログに記録し、続けます。 WorkflowServices アプリケーションを実行しようとしても、必要な構成設定がないため、実行することはできません。 たとえば、xoml やルール サービスの読み込みに失敗する可能性があります。  
  
 回避策を使用して、この問題、[ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)で、`/c`スイッチをコンピューターの IIS スクリプト マップを適切に構成します。 [ワークフロー サービス登録ツール (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\framework\v3.5\ または %windir%\Microsoft.NET\framework64\v3.5\ にあります  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>アセンブリ 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' から型 'System.ServiceModel.Activation.HttpModule' を読み込むことができない  
 このエラーが発生します[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]がインストールされているし、WCF HTTP アクティブ化が有効になっているとします。 Visual Studio の次のコマンド ラインから開発者コマンド プロンプト内で実行の問題を解決するには。  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>関連項目

- [セットアップ手順](../../../docs/framework/wcf/samples/set-up-instructions.md)
