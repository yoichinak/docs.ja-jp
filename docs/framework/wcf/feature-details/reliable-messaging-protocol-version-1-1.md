---
title: 信頼できるメッセージング プロトコル バージョン 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933992"
---
# <a name="reliable-messaging-protocol-version-11"></a>信頼できるメッセージング プロトコル バージョン 1.1
このトピックでは、Windows Communication Foundation (WCF) の実装の詳細を説明 WS-ReliableMessaging の 2007 年 2 月 (バージョン 1.1) プロトコルが HTTP トランスポートを使用して相互運用のために必要です。 WCF では、制約と明確にでは、このトピックで説明されている、WS-ReliableMessaging 仕様に従います。 以降では、WS-ReliableMessaging のバージョン 1.1 プロトコルを実装することに注意してください、[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]します。  
  
 WS-ReliableMessaging 2007 年 2 月での WCF でプロトコルが実装されている、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>します。  
  
 便宜上、ここでは次のロールを使用します。  
  
-   発信側:Ws-reliable メッセージ シーケンスの作成を開始するクライアント。  
  
-   レスポンダー:イニシエーターの要求を受信するサービスです。  
  
 このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。  
  
|プレフィックス|名前空間|  
|-|-|  
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|wsp|(WS-Policy 1.2 または WS-Policy 1.5 のいずれか)|  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="sequence-creation"></a>シーケンスの作成  
 WCF 実装`CreateSequence`と`CreateSequenceResponse`信頼性の高いメッセージングを確立するためにメッセージのシーケンスします。 以下の制約が適用されます。  
  
-   B1101:WCF イニシエーターとして同じエンドポイント参照を使用して、`CreateSequence`メッセージの`ReplyTo`、`AcksTo`と`Offer/Endpoint`します。  
  
-   R1102:`AcksTo`、`ReplyTo`と`Offer/Endpoint`エンドポイント参照、`CreateSequence`オクテットと一致するようにメッセージがまったく同じ文字列表現のアドレス値をいる必要があります。  
  
    -   確認します WCF 応答側の URI 部分、 `AcksTo`、`ReplyTo`と`Endpoint`シーケンスを作成する前に、エンドポイント参照は同じです。  
  
-   R1103:`AcksTo`、`ReplyTo`と`Offer/Endpoint`エンドポイント参照、`CreateSequence`メッセージは、参照パラメーターの同じセットを持つ必要があります。  
  
    -   WCF は強制されませんが、その参照を前提としていますのパラメーター、 `AcksTo`、`ReplyTo`と`Offer/Endpoint`エンドポイント参照にで`CreateSequence`と同じですが、参照パラメーターを使用して、`ReplyTo`のエンドポイント参照受信確認と逆方向シーケンス メッセージ。  
  
-   B1104:WCF のイニシエーターは、省略可能なは生成されません`Expires`または`Offer/Expires`内の要素、`CreateSequence`メッセージ。  
  
-   B1105:アクセスするとき、 `CreateSequence` WCF レスポンダーは、メッセージ、`Expires`値、`CreateSequence`要素として、`Expires`値、`CreateSequenceResponse`要素。 それ以外の場合、WCF 応答側の読み取り、無視、`Expires`と`Offer/Expires`値。  
  
-   B1106:アクセスするとき、`CreateSequenceResponse`メッセージ、WCF のイニシエーターは省略可能な読み取り`Expires`値が、これを使用しません。  
  
-   B1107:WCF のイニシエーターおよびレスポンダーは生成常に省略可能な`IncompleteSequenceBehavior`内の要素、`CreateSequence/Offer`と`CreateSequenceResponse`要素。  
  
-   B1108:WCF を使用してのみ、`DiscardFollowingFirstGap`と`NoDiscard`値、`IncompleteSequenceBehavior`要素。  
  
    -   WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構を利用しています。  
  
-   B1109:場合`CreateSequence`が含まれています、`Offer`で応答することの要素、一方向の WCF レスポンダー拒否シーケンス、`CreateSequenceResponse`せず、`Accept`要素。  
  
-   B1110:信頼できるメッセージング レスポンダーは、シーケンスを拒否する場合、WCF イニシエーター障害新しく確立されたシーケンスにします。  
  
-   B1111:場合`CreateSequence`が含まれていない、`Offer`で応答することの要素、双方向の WCF レスポンダー拒否シーケンス、`CreateSequenceRefused`エラー。  
  
-   R1112:使用して 2 つの逆方向シーケンスが確立されたときに、`Offer`メカニズム、`[address]`のプロパティ、`CreateSequenceResponse/Accept/AcksTo`エンドポイント参照は送信先 URI と一致する必要がありますの`CreateSequence`バイトのメッセージのバイト。  
  
-   R1113:使用して 2 つの逆方向シーケンスが確立されたときに、`Offer`メカニズム、イニシエーターからレスポンダーに送られて、両方のシーケンスのすべてのメッセージは、同じエンドポイント参照に送信する必要があります。  
  
 WCF では、WS-ReliableMessaging を使用して、イニシエーターとレスポンダー間の信頼できるセッションを確立します。 WCF の WS-ReliableMessaging 実装は、一方向、要求/応答、信頼できるセッションを提供します。 双方向メッセージング パターン。 `Offer` および `CreateSequence` で WS-ReliableMessaging の `CreateSequenceResponse` 機構を使用すると、相関する 2 つの逆方向シーケンスを確立できます。また、Offer 機構は、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。 WCF では、セッションのセッションの整合性をエンド ツー エンドの保護などのセキュリティ保証を提供するため、同じパーティ宛てのメッセージが同じ送信先に到達することを確認するは実用的です。 また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。 そのため、R1102、R1112、および R1113 の制約は、WCF に適用されます。  
  
 `CreateSequence` メッセージの例を次に示します。  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>  
    <wsa:ReplyTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>   
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>  
      </wsrm:AcksTo>  
      <wsrm:Offer>  
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>  
        <wsrm:Endpoint>  
          <wsa:Address>http://Business456.com/clientA</wsa:Address>  
        </wsrm:Endpoint>  
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      </wsrm:Offer>  
    </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 `CreateSequenceResponse` メッセージの例を次に示します。  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      <wsrm:Accept>  
        <wsrm:AcksTo>  
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>  
        </wsrm:AcksTo>  
      </wsrm:Accept>  
    </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="closing-a-sequence"></a>シーケンスを閉じる  
 WCF を使用して、`CloseSequence`と`CloseSequenceResponse`信頼性の高いメッセージング ソースが開始したシャット ダウンのメッセージ。 WCF の信頼できるメッセージング送信先はシャット ダウンを開始していないと、WCF の信頼性の高いメッセージの送信元が信頼できるメッセージング送信先が開始したシャット ダウンをサポートしていません。 以下の制約が適用されます。  
  
-   B1201:WCF の信頼性の高いメッセージの送信元を常に送信、`CloseSequence`メッセージ シーケンスをシャット ダウンします。  
  
-   B1202:信頼性の高いメッセージの送信元が送信する前に、シーケンス メッセージの完全な範囲の確認を待機、`CloseSequence`メッセージ。  
  
-   B1203:信頼できるメッセージング ソースに常には、省略可能な`LastMsgNumber`要素シーケンスにメッセージが含まれていない場合を除き、します。  
  
-   R1204:信頼性の高いメッセージの送信先を送信してシャット ダウンを開始する必要がありますいないを`CloseSequence`メッセージ。  
  
-   B1205:受信すると、`CloseSequence`メッセージ、WCF の信頼性の高いメッセージの送信元は不完全な順序を考慮し、エラーを送信します。  
  
 `CloseSequence` メッセージの例を次に示します。  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
    </wsrm:CloseSequence>  
  </s:Body>  
</s:Envelope>  
Example CloseSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:CloseSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence-termination"></a>シーケンスの終了  
 WCF は主に使用して、`TerminateSequence/TerminateSequenceResponse`ハンドシェイクが完了した後、`CloseSequence/CloseSequenceResponse`ハンドシェイクです。 WCF の信頼できるメッセージング送信先は終了を開始していないと、信頼性の高いメッセージの送信元が信頼できるメッセージング送信先が開始終了をサポートしていません。 以下の制約が適用されます。  
  
-   B1301:WCF イニシエーターのみを送信、`TerminateSequence`メッセージが正常に完了した後、`CloseSequence/CloseSequenceResponse`ハンドシェイクです。  
  
-   R1302:WCF の点を検証、`LastMsgNumber`要素がすべて間で一貫性のある`CloseSequence`と`TerminateSequence`特定のシーケンスのメッセージ。 つまり、`LastMsgNumber` は、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在しないか、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在し、同一であるかのいずれかです。  
  
-   B1303:受信するときに、`TerminateSequence`メッセージの後に、`CloseSequence/CloseSequenceResponse`ハンドシェイクで応答を信頼性の高いメッセージの送信先を`TerminateSequenceResponse`メッセージ。 信頼できるメッセージの配信元は、`TerminateSequence` メッセージを送信する前に最終受信確認を受けるため、信頼できるメッセージの送信先ではシーケンスが終了したことが確実にわかり、すぐにリソースを再要求します。  
  
-   B1304:受信するときに、`TerminateSequence`メッセージより前のバージョンを`CloseSequence/CloseSequenceResponse`ハンドシェイクで応答を WCF の信頼性の高いメッセージの送信先を`TerminateSequenceResponse`メッセージ。 信頼できるメッセージの送信先でシーケンスが一貫していると判断した場合、信頼できるメッセージの送信先は、リソースを再要求する前にアプリケーションの送信先で指定された時間待機し、クライアントが最終受信確認を受け取ることができるようにします。 それ以外の場合は、信頼できるメッセージの送信先はすぐにリソースを再要求し、`Faulted` イベントを発生させて、不明なシーケンスの終了をアプリケーションの送信先に示します。  
  
 `TerminateSequence` メッセージの例を次に示します。  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
      </wsrm:TerminateSequence>  
  </s:Body>  
</s:Envelope>  
Example TerminateSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:TerminateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequences"></a>シーケンス  
 シーケンスに適用される制約を以下に示します。  
  
-   B1401:WCF を生成し、アクセスのシーケンス番号より`xs:long`の最大の包含値 9223372036854775807 します。  
  
 `Sequence` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>受信確認の要求  
 WCF を使用して、 `AckRequested` keep-alive 機構としてヘッダー。  
  
 `AckRequested` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF では、Ws-reliable Messaging で提供されているシーケンス受信確認の「抱き合わせ」メカニズムを使用します。 以下の制約が適用されます。  
  
-   R1601:使用して 2 つの逆方向シーケンスが確立されたときに、`Offer`メカニズム、`SequenceAcknowledgement`目的の受信者に送信アプリケーション メッセージ ヘッダーを含めることができます。 リモートのエンドポイントは、追加された `SequenceAcknowledgement` ヘッダーにアクセスできる必要があります。  
  
-   B1602:WCF は生成されません`SequenceAcknowledgement`ヘッダーが含まれている`Nack`要素。 WCF では、その各を検証`Nack`要素は、シーケンス番号が含まれていますが、それ以外の場合は無視されます、`Nack`要素と値。  
  
 `SequenceAcknowledgement` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging エラー  
 次は、WS-ReliableMessaging エラーの WCF 実装に適用される制約の一覧です。 以下の制約が適用されます。  
  
-   B1701:WCF は生成されません`MessageNumberRollover`エラー。  
  
-   B1702:SOAP 1.2 では、経由でサービス エンドポイントは、接続の上限に達するし、新しい接続を処理することはできません WCF が生成されます、入れ子になった`CreateSequenceRefused`エラー サブコード`netrm:ConnectionLimitReached`次の例のようにします。  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>  
  </s:Header>  
  <s:Body>  
    <s:Fault>  
      <s:Code>  
        <s:Value>s:Receiver</s:Value>  
        <s:Subcode>  
          <s:Value>wsrm:CreateSequenceRefused</s:Value>  
          <s:Subcode>  
            <s:Value>netrm:ConnectionLimitReached</s:Value>  
          </s:Subcode>  
        </s:Subcode>  
      </s:Code>  
      <s:Reason>  
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>  
      </s:Reason>  
    </s:Fault>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="ws-addressing-faults"></a>WS-Addressing エラー  
 WS-ReliableMessaging は Ws-addressing を使用しているため、WCF の WS-ReliableMessaging 実装を生成して Ws-addressing エラーを送信する可能性があります。 このセクションでは、WCF は、明示的に生成し、WS-ReliableMessaging レイヤーで送信する Ws-addressing エラーについて説明します。  
  
-   B1801:WCF 生成し、送信、`Message Addressing Header Required`障害、次のいずれかが true の場合。  
  
    -   `CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `MessageId` ヘッダーがない。  
  
    -   `CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `ReplyTo` ヘッダーがない。  
  
    -   `CreateSequenceResponse`、`CloseSequenceResponse`、または `TerminateSequenceResponse` メッセージに `RelatesTo` ヘッダーがない。  
  
-   B1802:WCF 生成し、送信、`Endpoint Unavailable`をリッスンしているエンドポイントがないことを示すエラーでアドレス指定ヘッダーの検査に基づいてシーケンスを処理することができます、`CreateSequence`メッセージ。  
  
## <a name="protocol-composition"></a>プロトコル コンポジション  
  
### <a name="composition-with-ws-addressing"></a>WS-Addressing によるコンポジション  
 WCF には、Ws-addressing の 2 つのバージョンがサポートされています。Ws-addressing 2004/08 [WS-ADDR] と W3C Ws-addressing 1.0 の推奨事項 [WS ADDR コア] と [WS ADDR SOAP]。  
  
 WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。 WCF に適用される制約の一覧を次には。  
  
-   R2101:Ws-addressing 2004/08 と Ws-addressing 1.0 の両方を Ws-reliablemessaging で使用できます。  
  
-   R2102:特定の WS-ReliableMessaging シーケンス、またはを使用して関連付けられた逆方向シーケンスのペアを 1 つのバージョンの Ws-addressing を使用する必要があります、`Offer`メカニズム。  
  
### <a name="composition-with-soap"></a>SOAP によるコンポジション  
 WCF では、SOAP 1.1 と Ws-reliablemessaging で SOAP 1.2 の両方の使用をサポートします。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security と WS-SecureConversation によるコンポジション  
 WCF は、Ws-secure Conversation をセキュリティで保護されたトランスポート (HTTPS)、Ws-security によるコンポジション、およびコンポジションを使用して、WS-ReliableMessaging シーケンスを保護を提供します。 WS-ReliableMessaging 1.1 プロトコル、WS-Security 1.1、および WS-Secure Conversation 1.3 プロトコルは一緒に使う必要があります。 WCF に適用される制約の一覧を次には。  
  
-   R2301:WCF では、個々 のメッセージの整合性だけでなく、WS-ReliableMessaging シーケンスの整合性と機密性を保護するには、Ws-secure Conversation を使用する必要がある必要があります。  
  
-   R2302:AWS-WS-ReliableMessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。  
  
-   R2303:WS-ReliableMessaging シーケンスの有効期間がセッションの有効期間、Ws-secure Conversation を超えた場合、 `SecurityContextToken` Ws-secure Conversation は、対応する Ws-secure Conversation の更新のバインドを使用して更新する必要がありますを使用して確立されます。  
  
-   B2304:WS-ReliableMessaging シーケンスまたは相関する逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。  
  
-   R2305:WCF 応答側がある必要がありますで Ws-secure Conversation で構成されているときに、`CreateSequence`メッセージが含まれて、`wsse:SecurityTokenReference`要素と`wsrm:UsesSequenceSTR`ヘッダー。  
  
 `UsesSequenceSTR` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>SSL/TLS セッションによるコンポジション  
 WCF は、SSL/TLS セッションによるコンポジションをサポートしていません。  
  
-   B2401:WCF は生成されません、`wsrm:UsesSequenceSSL`ヘッダー。  
  
-   R2402:信頼性の高いメッセージングの発信側が送信する必要があります、`CreateSequence`メッセージである、 `wsrm:UsesSequenceSSL` WCF レスポンダーにヘッダー。  
  
### <a name="composition-with-ws-policy"></a>WS-Policy によるコンポジション  
 WCF には、Ws-policy の 2 つのバージョンがサポートされています。Ws-policy 1.2 および Ws-policy 1.5 の場合は。  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging の WS-Policy アサーション  
 WS-ReliableMessaging の Ws-policy アサーションを使用する WCF`wsrm:RMAssertion`エンドポイントの機能を記述します。 WCF に適用される制約の一覧を次には。  
  
-   B3001:WCF のアタッチ`wsrmn:RMAssertion`Ws-policy アサーションを`wsdl:binding`要素。 WCF では、両方の添付ファイルを`wsdl:binding`と`wsdl:port`要素。  
  
-   B3002:WCF では生成されません、`wsp:Optional`タグ。  
  
-   B3003:アクセスするとき、 `wsrmp:RMAssertion` Ws-policy アサーションでは、WCF は無視されます、`wsp:Optional`タグ付けし、WS-RM ポリシーを必須として扱われます。  
  
-   R3004:WCF を指定するポリシーを受け付けません WCF は、SSL/TLS セッションでは構成できません、ため`wsrmp:SequenceTransportSecurity`します。  
  
-   B3005:WCF は常に生成、`wsrmp:DeliveryAssurance`要素。  
  
-   B3006:WCF は常を指定します、`wsrmp:ExactlyOnce`配信が保証されます。  
  
-   B3007:WCF が生成されます、WS-ReliableMessaging アサーションの以下のプロパティを読み取るし、WCF の上にコントロールを提供します`ReliableSessionBindingElement`:。  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     `RMAssertion` の例を次に示します。  
  
    ```xml  
    <wsrmp:RMAssertion>  
      <wsp:Policy>  
        <wsrmp:SequenceSTR/>  
        <wsrmp:DeliveryAssurance>  
          <wsp:Policy>  
            <wsrmp:ExactlyOnce/>  
            <wsrmp:InOrder/>  
          </wsp:Policy>  
        </wsrmp:DeliveryAssurance>  
      </wsp:Policy>  
      <netrmp:InactivityTimeout Milliseconds="600000"/>  
      <netrmp:AcknowledgementInterval Milliseconds="200"/>  
    </wsrmp:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>WS-ReliableMessaging のフロー制御拡張  
 WCF では、WS-ReliableMessaging の機能拡張を使用して、シーケンス メッセージ フローを省略可能なさらに厳密な制御を提供します。  
  
 フロー制御が有効になって、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType>プロパティを`true`します。 WCF に適用される制約の一覧を次には。  
  
-   B4001:信頼できるメッセージング フロー制御を有効にすると、WCF が生成されます、`netrm:BufferRemaining`内の要素拡張の要素、`SequenceAcknowledgement`ヘッダー、次の例に示すようにします。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002:信頼できるメッセージング フロー制御が有効になっている場合でも、WCF は必要ありません、`netrm:BufferRemaining`内の要素、`SequenceAcknowledgement`ヘッダー。  
  
-   B4003:信頼できるメッセージング送信先の WCF を使用して`netrm:BufferRemaining`を新しいメッセージの数にする方法を示すために入れることができます。  
  
-   B4004:When 信頼できるメッセージング フロー制御が有効になっているの値を使用する WCF の信頼性の高いメッセージング ソース`netrm:BufferRemaining`スロットル メッセージを転送します。  
  
-   B4005:WCF が生成されます`netrm:BufferRemaining`整数 0 ~ 4096 の範囲、範囲の値し、0 までの整数値を読み取ると`xs:int`の`maxInclusive`214748364 の値します。  
  
## <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 このセクションでは、WS-ReliableMessaging をさまざまなメッセージ交換パターンを使用する場合、WCF の動作が説明します。 各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。  
  
-   アドレス不可能なイニシエーター:イニシエーターが; ファイアウォールの背後にはレスポンダーは、HTTP 応答でのみイニシエーターにメッセージを配信できます。  
  
-   アドレス指定可能なイニシエーター:イニシエーターおよびレスポンダーは HTTP 要求を送信します。つまり、2 つの逆方向の HTTP 接続を確立できます。  
  
### <a name="one-way-non-addressable-initiator"></a>一方向 : アドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF には、1 つの HTTP チャネル経由で 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用してレスポンダーからイニシエーターにすべてのメッセージを送信する応答側および HTTP 応答に、発信側からのすべてメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF 発信側が送信を`CreateSequence`なしでメッセージ`Offer`要素は、HTTP 要求で想定されている、 `CreateSequenceResponse` HTTP 応答でメッセージ。 WCF 応答側はシーケンスを作成し、送信、`CreateSequenceResponse`のないメッセージ`Accept`HTTP 応答での要素。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF のイニシエーターを除くすべてのメッセージの返信の受信確認の処理、`CreateSequence`メッセージとエラー メッセージ。 WCF 応答側が常にすべてのシーケンスに、HTTP 応答でスタンドアロンの受信確認を送信し、`AckRequested`メッセージ。  
  
#### <a name="closesequence-exchange"></a>CloseSequence の交換  
 WCF の発信側の送信、 `CloseSequence` 、HTTP 要求でメッセージ、 `CreateSequenceResponse` HTTP 応答でメッセージ。 WCF 応答側の送信、`CloseSequenceResponse`で HTTP 応答メッセージ。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 WCF の発信側の送信、 `TerminateSequence` 、HTTP 要求でメッセージ、 `TerminateSequenceResponse` HTTP 応答でメッセージ。 WCF 応答側の送信、`TerminateSequenceResponse`で HTTP 応答メッセージ。  
  
### <a name="one-way-addressable-initiator"></a>一方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF は、1 つに 1 つのシーケンスを使用して一方向メッセージ交換パターンを提供します。 受信と送信の 1 つの HTTP チャネル。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側が送信を`CreateSequence`メッセージなしで`Offer`HTTP 要求での要素。 WCF 応答側はシーケンスを作成し、送信、`CreateSequenceResponse`メッセージなしで`Accept`HTTP 要求での要素。  
  
### <a name="duplex-addressable-initiator"></a>双方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF では、2 つを使用して、完全に非同期の双方向メッセージ交換パターンをシーケンス 1 つ以上用意されています受信と送信の 1 つの HTTP チャネル。 このメッセージ交換パターンは、限定された方法で `Request/Reply`、`Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側が送信を`CreateSequence`メッセージである、 `Offer` HTTP 要求での要素。 WCF 応答側により、`CreateSequence`が、`Offer`要素: シーケンスを作成し、送信、`CreateSequenceResponse`メッセージである、`Accept`要素。  
  
#### <a name="sequence-lifetime"></a>シーケンスの有効期間  
 2 つのシーケンスは、WCF は、1 つの完全な双方向セッションとして扱います。  
  
 1 つのシーケンスをフォールトするエラーを生成すると WCF には、両方のシーケンスをフォールトするリモート エンドポイントが必要です。 WCF の障害を 1 つのシーケンスをフォールトするエラーを読んだときに両方のシーケンスします。  
  
 WCF は、送信シーケンスを閉じるし、受信シーケンスでのメッセージの処理を続行することができます。 逆に、WCF は、受信シーケンスの終了を処理して、送信シーケンスでメッセージを送信し続けます。  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>要求/応答および一方向のアドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF は、一方向と、要求/応答メッセージ交換のパターンを使用して 2 つのシーケンスの 1 つの HTTP チャネル。 WCF では、HTTP 要求を使用してレスポンダーからイニシエーターにすべてのメッセージを送信する応答側および HTTP 応答に、発信側からのすべてメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側が送信、`CreateSequence`メッセージである、 `Offer` 、HTTP 要求で要素が必要ですが、 `CreateSequenceResponse` HTTP 応答でメッセージ。 WCF 応答側はシーケンスを作成し、送信、`CreateSequenceResponse`メッセージである、 `Accept` HTTP 応答での要素。  
  
#### <a name="one-way-message"></a>一方向のメッセージ  
 一方向メッセージ交換を正常に完了するには、WCF のイニシエーターは HTTP 要求で要求シーケンス メッセージ送信し、スタンドアロンの受信`SequenceAcknowledgement`で HTTP 応答メッセージ。 `SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。  
  
 WCF 応答側は、受信確認、エラー、または空の本文と HTTP 202 ステータス コードを含む応答で要求に返信があります。  
  
#### <a name="two-way-messages"></a>双方向のメッセージ  
 双方向のメッセージ交換プロトコルを正常に完了するは、WCF イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。 応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。  
  
 WCF 応答側は、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードを含む応答で要求に返信があります。  
  
 一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。  
  
#### <a name="retrying-replies"></a>応答の再試行  
 WCF は、双方向メッセージ交換プロトコルの相関関係の HTTP 要求-応答の相関関係に依存します。 このため、WCF のイニシエーターは、停止されませんが、要求シーケンス メッセージが受信確認されるときに、要求シーケンス メッセージの再試行ではなく HTTP 応答を実行すると、 `SequenceAcknowledgement`、アプリケーション応答、またはエラー。 WCF 応答側は、応答が関連付けられている要求の HTTP 応答で応答を再試行します。  
  
#### <a name="closesequence-exchange"></a>CloseSequence の交換  
 WCF のイニシエーターを送信するすべての応答シーケンス メッセージおよび一方向の要求シーケンスのすべてのメッセージに対する受信確認を受信した後、 `CloseSequence` 、HTTP 要求で要求シーケンス メッセージ、 `CloseSequenceResponse` HTTP 応答でします。  
  
 要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。 WCF イニシエーターには、応答シーケンスの最後が含まれています。 つまり`SequenceAcknowledgement`上、`CloseSequence`メッセージと応答シーケンスがない、 `CloseSequence` exchange。  
  
 WCF 応答側により、すべての返信は、受信確認し、送信、`CloseSequenceResponse`で HTTP 応答メッセージ。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 受信した後、`CloseSequenceResponse`メッセージ、WCF の発信側の送信、 `TerminateSequence` 、HTTP 要求で要求シーケンス メッセージ、 `TerminateSequenceResponse` HTTP 応答でします。  
  
 `CloseSequence` 交換と同じように、要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。 WCF イニシエーターには、応答シーケンスの最後が含まれています。 つまり`SequenceAcknowledgement`上、`TerminateSequence`メッセージと応答シーケンスがない、 `TerminateSequence` exchange。  
  
 WCF 応答側の送信、`TerminateSequenceResponse`で HTTP 応答メッセージ。  
  
### <a name="requestreply-addressable-initiator"></a>要求/応答 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF は、要求/応答メッセージ交換パターンを使用して 2 つのシーケンスの 1 つ以上受信と送信の 1 つの HTTP チャネル。 このメッセージ交換パターンは、限定された方法で `Duplex, Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側が送信を`CreateSequence`メッセージである、 `Offer` HTTP 要求での要素。 WCF 応答側により、`CreateSequence`が、`Offer`要素: シーケンスを作成し、送信、`CreateSequenceResponse`メッセージである、`Accept`要素。  
  
#### <a name="requestreply-correlation"></a>要求/応答の相関関係  
 次の状況は、すべての相関関係にある要求/応答で発生します。  
  
-   WCF により、すべてのアプリケーション要求メッセージの熊、`ReplyTo`エンドポイント参照と`MessageId`します。  
  
-   WCF では、各アプリケーション要求メッセージのとしてローカル エンドポイント参照を適用`ReplyTo`します。 ローカル エンドポイント参照は、イニシエーターの `CreateSequence` メッセージの `ReplyTo` であり、レスポンダーの `CreateSequence` メッセージの `To` です。  
  
-   WCF により、その着信要求メッセージの熊、`MessageId`と`ReplyTo`します。  
  
-   WCF により、`ReplyTo`に定義されているすべてのアプリケーション要求メッセージのエンドポイント参照の URI がローカル エンドポイント参照に一致します。  
  
-   WCF では、すべての応答が正しい負うことにより、`RelatesTo`と`To`に従ってヘッダー`wsa`要求/応答の相関ルール。
