---
title: '方法: ネットワークのトレースを構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: dc9b6b5399063026c0bbe5735964ed42a21168fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048368"
---
# <a name="how-to-configure-network-tracing"></a>方法: ネットワークのトレースを構成する
アプリケーションまたはコンピューターの構成ファイルには、ネットワークのトレースの形式と内容を決定する設定が保持されます。 この手順に従う前に、トレースが有効になっていることを確認します。 トレースの有効化については、「[ネットワークのトレースの有効化](enabling-network-tracing.md)」を参照してください。  
  
 コンピューター構成ファイルの machine.config は、Windows をインストールしたディレクトリの %Windir%\Microsoft.NET\Framework フォルダーに格納されます。 コンピューターにインストールされた .NET Framework のバージョンごとに、%Windir%\Microsoft.NET\Framework の下のフォルダーに別々の machine.config ファイルがあります (例: C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config または C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config)。  
  
 これらの設定は、コンピューター構成ファイルよりも優先されるアプリケーション構成ファイルでも行うことができます。  
  
### <a name="to-configure-network-tracing"></a>ネットワークのトレースを構成するには  
  
- 適切な構成ファイルに次の行を追加します。 これらの設定の値とオプションを次の表に示します。  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="System.Net" tracemode="includehex" maxdatasize="1024">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Cache">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Http">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Sockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.WebSockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="System.Net" value="Verbose"/>  
          <add name="System.Net.Cache" value="Verbose"/>  
          <add name="System.Net.Http" value="Verbose"/>  
          <add name="System.Net.Sockets" value="Verbose"/>  
          <add name="System.Net.WebSockets" value="Verbose"/>  
        </switches>  
        <sharedListeners>  
          <add name="System.Net"  
            type="System.Diagnostics.TextWriterTraceListener"  
            initializeData="network.log"
            traceOutputOptions="ProcessId, DateTime" 
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 `<switches>` ブロックに名前を追加すると、トレース出力にその名前に関連する一部のメソッドからの情報が含まれます。 次の表に出力を示します。  
  
|name|出力元|  
|----------|-----------------|  
|`System.Net.Sockets`|<xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.TcpClient>、および <xref:System.Net.Dns> クラスの一部のパブリック メソッド。|  
|`System.Net`|<xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>、<xref:System.Net.FtpWebRequest>、および <xref:System.Net.FtpWebResponse> クラスの一部のパブリック メソッド、および SSL デバッグ情報 (無効な証明書、不足している発行元一覧、およびクライアント証明書エラー)。|  
|`System.Net.HttpListener`|<xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest>、および <xref:System.Net.HttpListenerResponse> クラスの一部のパブリック メソッド。|  
|`System.Net.Cache`|`System.Net.Cache` 内の一部のプライベート メソッドと内部メソッド。|  
|`System.Net.Http`|<xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler>、および <xref:System.Net.Http.WebRequestHandler> クラスの一部のパブリック メソッド。|  
|`System.Net.WebSockets.WebSocket`|<xref:System.Net.WebSockets.ClientWebSocket> および <xref:System.Net.WebSockets.WebSocket> クラスの一部のパブリック メソッド。|  
  
 次の表に示した属性で、トレース出力の書式を設定します。  
  
|属性名|属性値|  
|--------------------|---------------------|  
|`Value`|必須の <xref:System.String> 属性です。 出力の詳細度を設定します。 有効な値は、`Critical`、`Error`、`Verbose`、`Warning`、および `Information` です。<br /><br /> この属性は、この例に示すように、\<switches> 要素の \<add name> 要素で設定する必要があります。 この属性を \<source> 要素で設定すると、例外がスローされます。|  
|`maxdatasize`|省略可能な <xref:System.Int32> 属性です。 各行トレースに含まれるネットワーク データの最大バイト数を設定します。 既定値は 1024 です。<br /><br /> この属性は、この例に示すように、\<source> 要素で設定する必要があります。 この属性を \<switches> 要素の下の要素で設定すると、例外がスローされます。|  
|`Tracemode`|省略可能な <xref:System.String> 属性です。 プロトコル トレースを 16 進数およびテキストの形式で表示するには、`includehex` に設定します。 テキストのみを表示するには、`protocolonly` に設定します。 既定値は `includehex` です。<br /><br /> この属性は、この例に示すように、\<switches> 要素で設定する必要があります。 この属性を \<source> 要素の下の要素で設定すると、例外がスローされます。|  
  
## <a name="see-also"></a>関連項目

- [ネットワークのトレースの解釈](interpreting-network-tracing.md)
- [.NET Framework のネットワークのトレース](network-tracing.md)
- [ネットワークのトレースの有効化](enabling-network-tracing.md)
- [アプリケーションのトレースとインストルメント](../debug-trace-profile/tracing-and-instrumenting-applications.md)
