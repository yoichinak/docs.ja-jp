---
title: WIF および Web ファーム
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 32d2875ebe0a46b9f9b1856ed70a30114793e492
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045250"
---
# <a name="wif-and-web-farms"></a>WIF および Web ファーム
Windows Identity Foundation (WIF) を使用して、Web ファームに展開されている証明書利用者 (RP) アプリケーションのリソースをセキュリティで保護するには、ファーム内の別のコンピューターで実行されている RP アプリケーションのインスタンスのトークンを WIF が処理できるように、特定の手順を実行する必要があります。 この処理には、セッション トークン シグネチャの検証、セッション トークンの暗号化と復号化、再生されたセキュリティ トークンの検出が含まれます。  
  
 一般的に、(RP が単一のコンピューターで実行されているか、Web ファームで実行されているかにかかわらず) RP アプリケーションのリソースをセキュリティで保護するために WIF を使用する場合、セキュリティ トークン サービス (STS) から取得されたセキュリティ トークンに基づいて、クライアントとの間にセッションが確立します。 これは、WIF を使用して保護されているすべてのアプリケーション リソースについて、STS での認証をクライアントに強制することを避けるためです。 WIF がセッションを処理する方法については、「[WIF Session Management](wif-session-management.md)」(WIF セッション管理) を参照してください。  
  
 既定の設定が使用される場合、WIF は次の処理を実行します。  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> クラスのインスタンスを使用して、認証に使用されたセキュリティ トークンに関するクレームや他の情報を格納するセッション トークン (<xref:System.IdentityModel.Tokens.SessionSecurityToken> クラスのインスタンス) の読み取りと書き込みを行います。 セッション トークンはパッケージ化され、セッション Cookie に格納されます。 既定で <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> は <xref:System.IdentityModel.ProtectedDataCookieTransform> クラスを使用します。このクラスはデータ保護 API (DPAPI) を使用してセッション トークンを保護します。 DPAPI は、ユーザーまたはコンピューターの資格情報を使用して保護を実装し、ユーザー プロファイルにキー データを格納します。  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> クラスの既定のメモリ内実装を使用して、セッション トークンを格納し、処理します。  
  
 これらの既定の設定は、RP アプリケーションが単一のコンピューターに展開されるシナリオで機能します。一方、Web ファームに展開する場合、各 HTTP 要求は、別のコンピューターで実行されている RP アプリケーションの別インスタンスに送信され、処理される可能性があります。 このシナリオでは、前述の既定の WIF 設定は機能しません。これは、トークンの保護とトークンのキーボード ショートカットの両方が特定のコンピューターに依存しているためです。  
  
 Web ファームに RP アプリケーションを展開するには、セッション トークン (および再生されたトークン) の処理が、特定のコンピューターで実行されているアプリケーションに依存していないことを確認する必要があります。 これを確認するには、ASP.NET の `<machineKey>` 構成要素に用意されている機能を使用し、セッション トークンと再生されたトークンに分散キャッシュを利用するように RP アプリケーションを実装する方法があります。 `<machineKey>` 要素を使用すると、構成ファイル内のトークンの検証、暗号化、および復号化に必要なキーを指定できます。これにより、Web ファーム内の別のコンピューターで同じキーを指定できるようになります。 WIF には、<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> という特殊なセッション トークン ハンドラーがあります。このハンドラーは、`<machineKey>` 要素に指定されているキーを使用してトークンを保護します。 この戦略を実施する場合は、次のガイドラインに従うことをお勧めします。  
  
- 構成で ASP.NET の `<machineKey>` 要素を使用して、ファーム内のコンピューター全体で使用できる署名および暗号化キーを明示的に指定します。 次の XML は、構成ファイルの `<system.web>` 要素以下の `<machineKey>` 要素の指定を示しています。  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- トークン ハンドラー コレクションに追加することで、<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> を使用するようにアプリケーションを構成します。 このようなハンドラーが存在する場合は、まず <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (または <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> クラスから派生した任意のハンドラー) をトークン ハンドラー コレクションから削除する必要があります。 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> は <xref:System.IdentityModel.Services.MachineKeyTransform> クラスを使用します。このクラスは、`<machineKey>` 要素に指定された暗号化マテリアルを使用して、セッション Cookie データを保護します。 次の XML は、<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> をトークン ハンドラー コレクションに追加する方法を示しています。  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> から派生させ、分散キャッシュを実装します。つまり、RP が実行される可能性があるファーム内のすべてのコンピューターからアクセスできるキャッシュです。 構成ファイルに [\<sessionSecurityTokenCache>](../configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 要素を指定して、分散キャッシュを使用するように RP を構成します。 必要に応じて、派生クラスの <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> メソッドをオーバーライドして、`<sessionSecurityTokenCache>` 要素の子要素を実装することができます。  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     分散キャッシュを実装するには、カスタム キャッシュ用に WCF フロント エンドを用意する方法があります。 WCF キャッシュ サービスの詳細については、「[WCF キャッシュ サービス](#BKMK_TheWCFCachingService)」を参照してください。 キャッシュ サービスを呼び出すために RP アプリケーションが使用できる WCF クライアントの実装の詳細については、「[WCF キャッシュ クライアント](#BKMK_TheWCFClient)」を参照してください。  
  
- アプリケーションで再生されたトークンを検出する場合、<xref:System.IdentityModel.Tokens.TokenReplayCache> から派生させ、[\<tokenReplayCache>](../configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) 構成要素内のトークン再生キャッシュ サービスを示すことで、トークン再生キャッシュの場合に同様の分散キャッシュ戦略に従う必要があります。  
  
> [!IMPORTANT]
> このトピックの XML とコード例はすべて、 [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408)サンプルから取得されています。  
  
> [!IMPORTANT]
> このトピックの例は変更せずに提供されています。また、変更せずに実稼働コードで使用しないでください。  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>WCF キャッシュ サービス  
 次のインターフェイスでは、証明書利用者アプリケーションが使用している WCF キャッシュ サービスと WCF クライアント間のコントラクトを定義して通信します。 これは、実質的にサービス操作として <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> クラスのメソッドを公開するものです。  
  
```csharp
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 WCF キャッシュ サービスの実装を次のコードに示します。 この例では、WIF に実装されている既定のメモリ内セッション トークン キャッシュが使用されます。 または、データベースに基づく永続的なキャッシュを実装することもできます。 `ISessionSecurityTokenCacheService` で、上記のインターフェイスを定義します。 この例では、簡略化のために、インターフェイスの実装に必要なメソッドのすべてを示していません。  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a>WCF キャッシュ クライアント  
 このセクションでは、<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> から派生し、呼び出しをキャッシュ サービスにデリゲートするクラスの実装について説明します。 次の XML のように、[\<sessionSecurityTokenCache>](../configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 要素でこのクラスを使用するように RP アプリケーションを構成します。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 このクラスは <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> メソッドをオーバーライドし、`<sessionSecurityTokenCache>` 要素のカスタム `<cacheServiceAddress>` 子要素からサービス エンドポイントを取得します。 このエンドポイントを使用して、サービスとの通信に使用する `ISessionSecurityTokenCacheService` チャネルを初期化します。  この例では、簡略化のために、<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> クラスの実装に必要なメソッドのすべてを示していません。  
  
```csharp
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [WIF セッション管理](wif-session-management.md)
