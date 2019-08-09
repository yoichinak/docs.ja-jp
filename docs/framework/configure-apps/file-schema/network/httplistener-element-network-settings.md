---
title: <httpListener> 要素 (ネットワーク設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 8257b0311e18a21fbc04185f8297ee8e5f38b86b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592741"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener> 要素 (ネットワーク設定)
<xref:System.Net.HttpListener>クラスで使用されるパラメータをカスタマイズします。  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<httpListener>  
  
## <a name="syntax"></a>構文  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>型  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|unescapeRequestUrl|場合を示すブール値、<xref:System.Net.HttpListener>インスタンスは、変換された URI ではなく生のエスケープ解除された URI を使用します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>Remarks  
 **UnescapeRequestUrl**属性を示す場合<xref:System.Net.HttpListener>をパーセントでエンコードされた値は変換され、その他の正規化の手順を実行、変換された URI ではなく生のエスケープ解除された URI を使用します。  
  
 ときに、<xref:System.Net.HttpListener>インスタンスを介して要求を受け取ると、`http.sys`により指定された URI 文字列のインスタンスを作成しますが、サービス`http.sys`、としてそれを公開、<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>プロパティ。  
  
 `http.sys`サービスは 2 つの要求 URI の文字列を公開します。  
  
- 生の URI  
  
- 変換された URI  
  
 生の URI は、 <xref:System.Uri?displayProperty=nameWithType> HTTP 要求の要求行で提供されます。  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 によって提供された生の URI`http.sys`上記のように、要求は"パス"/です。 これは、次の HTTP 動詞がネットワーク経由で送信した文字列を表します。  
  
 `http.sys`サービスは、HTTP 要求行で指定された URI を使用して、要求で提供される情報から変換された URI を作成しに、要求の配信元サーバーを決定する、ホスト ヘッダーを転送する必要があります。 これは、一連の登録済みの URI プレフィックスを使用して要求からの情報を比較することによって行います。 この変換された URI は、HTTP Server SDK ドキュメントでは HTTP_COOKED_URL 構造と呼びます。  
  
 登録済みの URI プレフィックスを持つ要求を比較できるようにするには、するには、要求の正規化をいくつかを実行する必要があります。 変換された URI 上のサンプルであるように。  
  
 `http://www.contoso.com/path/`  
  
 `http.sys`サービスの結合、<xref:System.Uri.Host%2A?displayProperty=nameWithType>プロパティの値と、変換された URI を作成する要求の行の文字列。 さらに、`http.sys`と<xref:System.Uri?displayProperty=nameWithType>クラスも、次を行います。  
  
- すべてのパーセントでエンコードされた値エスケープ解除します。  
  
- Utf-16 文字表現に非 ASCII 文字をパーセントでエンコードに変換します。 Unicode の文字 (Unicode のエンコード %uxxxx 形式を使用) と、utf-8 と ANSI や DBCS 文字がサポートされていることに注意してください。  
  
- パスの圧縮など、他の正規化の手順を実行します。  
  
 要求には、パーセントでエンコードされた値に使用されるエンコーディングに関する情報が含まれていない、以降は、パーセントでエンコードされた値を解析するだけで正しいエンコーディングを判断することはできません。  
  
 そのため`http.sys`プロセスを変更するための 2 つのレジストリ キーを提供します。  
  
|レジストリ キー|既定値|説明|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|0 の場合、 `http.sys` UTF エンコードの Url のみを受け入れます。<br /><br /> 0 以外の場合`http.sys`も要求で ANSI でエンコードされたまたは DBCS でエンコードされた Url を受け取ります。|  
|FavorUTF8|1|0 以外の場合`http.sys`最初をデコードする URL を utf-8 として; 変換に失敗したし、EnableNonUTF8 が 0 以外の場合と常に、Http.sys、ANSI または DBCS とデコードを試みます。<br /><br /> 0 の場合 (および EnableNonUTF8 が 0 以外)、`http.sys`を ANSI または DBCS; としてデコードする試行が成功しなかった、utf-8 変換を試みます。|  
  
 ときに<xref:System.Net.HttpListener>要求を受信から変換された URI を使用して`http.sys`への入力として、<xref:System.Net.HttpListenerRequest.Url%2A>プロパティ。  
  
 Uri の文字と数字以外の文字をサポートする必要があります。 例としては、次の URI は、お客様の顧客情報を取得するために使用番号「1/3812」。  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Uri (%2f) でパーセント エンコード スラッシュに注意してください。 これは、スラッシュ文字を表すデータとパス区切り記号ではなくこのケースであるため、必要に応じて。  
  
 Uri のコンス トラクターに文字列を渡すことは、次の URI につながります。  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 パスはセグメントに分割することで、次の要素になります。  
  
 `Customer('1`  
  
 `3812')`  
  
 これは、要求の送信元の目的ではありません。  
  
 場合、 **unescapeRequestUrl**属性に設定されて**false**、その後、<xref:System.Net.HttpListener>要求を受信から変換された URI ではなく生の URI を使用して`http.sys`への入力として<xref:System.Net.HttpListenerRequest.Url%2A>プロパティ。  
  
 既定値、 **unescapeRequestUrl**属性が**true**します。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>プロパティを使用しての現在の値を取得すること、 **unescapeRequestUrl**該当する構成ファイルからの属性。  
  
## <a name="example"></a>例  
 次の例は、構成する方法を示します、<xref:System.Net.HttpListener>から変換された URI ではなく生の URI を使用して要求を受信時`http.sys`への入力として、<xref:System.Net.HttpListenerRequest.Url%2A>プロパティ。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||
|-|-|  
|名前空間|System.Net|  
|スキーマ名||  
|検証ファイル||  
|空にすることができます。||  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
