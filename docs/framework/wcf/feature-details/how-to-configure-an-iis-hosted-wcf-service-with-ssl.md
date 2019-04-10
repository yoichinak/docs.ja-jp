---
title: '方法: IIS でホストされる WCF サービスに SSL を構成する'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 336c3800fc033cc12bd9c3fe168ae219b72cab91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214119"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>方法: IIS でホストされる WCF サービスに SSL を構成する
ここでは、HTTP トランスポート セキュリティを使用するように IIS でホストされる WCF サービスをセットアップする方法について説明します。 HTTP トランスポート セキュリティを使用するには、SSL 証明書が IIS に登録されている必要があります。 SSL 証明書がない場合は、IIS を使用してテスト証明書を生成できます。 次に、Web サイトに SSL バインディングを追加し、Web サイトの認証プロパティを構成する必要があります。 最後に、HTTPS を使用するように WCF サービスを構成する必要があります。  
  
### <a name="creating-a-self-signed-certificate"></a>自己署名証明書の作成  
  
1.  インターネット インフォメーション サービス マネージャー (inetmgr.exe) を開き、左側のツリー ビューでコンピューター名を選択します。 画面の右側で [サーバー証明書] を選択します。  
  
     ![IIS マネージャーのホーム画面](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  サーバー証明書 ウィンドウで、**自己署名証明書を作成しています.** リンクをクリックします。  
  
     ![自動作成&#45;署名入り証明書を IIS に](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  自己署名証明書のフレンドリ名を入力し、クリックして**OK**します。  
  
     ![作成自己&#45;署名証明書ダイアログ](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     新しく作成された自己署名証明書の詳細はここで示した、**サーバー証明書**ウィンドウ。  
  
     ![サーバー証明書 ウィンドウ](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     生成された証明書が、信頼されたルート証明機関ストアにインストールされます。  
  
### <a name="add-ssl-binding"></a>SSL バインドの追加  
  
1.  インターネット インフォメーション サービス マネージャーでも、展開、**サイト**フォルダーをクリックし、**既定の Web サイト**画面の左側にあるツリー ビュー内のフォルダー。  
  
2.  をクリックして、**バインドしています.** 内のリンク、**アクション**ウィンドウの右上部分でセクション。  
  
     ![SSL バインドの追加](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  サイト バインド ウィンドウで、**追加**ボタンをクリックします。  
  
     ![サイト バインド ダイアログ ボックス](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  **サイト バインドの追加**ダイアログ ボックスで、型とした自己署名証明書のフレンドリ名に対する https の選択を作成します。  
  
     ![サイト バインドの例](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>SSL の仮想ディレクトリの構成  
  
1.  インターネット インフォメーション サービス マネージャーで、WCF のセキュリティで保護されたサービスが含まれている仮想ディレクトリを選択します。  
  
2.  ウィンドウの中央のウィンドウで次のように選択します。 **SSL 設定**IIS セクションでします。  
  
     ![仮想ディレクトリの SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  SSL 設定 ウィンドウで、選択、 **SSL が必要**チェック ボックスをオン をクリックし、**適用**のリンクを**アクション**画面の右側にあるセクション。  
  
     ![仮想ディレクトリの SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>HTTP トランスポート セキュリティのための WCF サービスの構成  
  
1.  WCF サービスの Web.config で、次の XML に示すように、トランスポート セキュリティを使用するよう HTTP バインドを構成します。  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2.  次の XML に示すように、サービスとサービス エンドポイントを指定します。  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a>例  
 次は、HTTP トランスポート セキュリティを使用した WCF サービスの web.config ファイルの詳細な例です。  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [インターネット インフォメーション サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [インターネット インフォメーション サービスのホスティング手順](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [インライン コードを使用した IIS ホスティング](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
