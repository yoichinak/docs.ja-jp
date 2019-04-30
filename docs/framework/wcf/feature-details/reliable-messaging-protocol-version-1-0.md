---
title: 信頼できるメッセージング プロトコル バージョン 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 02a0815f62999c27507ed5e1610f090e944c135a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946706"
---
# <a name="reliable-messaging-protocol-version-10"></a>信頼できるメッセージング プロトコル バージョン 1.0
このトピックでは、Windows Communication Foundation (WCF) の実装の詳細を説明 Ws-reliable メッセージングの 2005 年 2 月 (バージョン 1.0) プロトコルが HTTP トランスポートを使用して相互運用のために必要です。 WCF では、制約と明確にでは、このトピックで説明されている Ws-reliablemessaging 仕様に従います。 WS-ReliableMessaging バージョン 1.0 プロトコルは、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 以降に実装されています。  
  
 Ws-reliablemessaging 2005 年 2 月での WCF でプロトコルが実装されている、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>します。  
  
 便宜上、ここでは次のロールを使用します。  
  
- イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント  
  
- レスポンダー : イニシエーターの要求を受け取るサービス  
  
 このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。  
  
|プレフィックス|名前空間|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="sequence-establishment-messages"></a>シーケンス確立メッセージ  
 WCF 実装`CreateSequence`と`CreateSequenceResponse`メッセージを信頼性の高いメッセージ シーケンスを確立します。 以下の制約が適用されます。  
  
- B1101:WCF のイニシエーターは、オプションの Expires 要素を生成しません、`CreateSequence`メッセージまたはの場合と、`CreateSequence`メッセージが含まれています、`Offer`要素、省略可能な`Expires`内の要素、`Offer`要素。  
  
- B1102:アクセスするとき、`CreateSequence`メッセージが WCF`Responder`は送受信両方`Expires`要素が存在する相手は、その値を使用しない場合。  
  
 WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構が導入されています。  
  
- R1103:場合`CreateSequence`が含まれています、 `Offer` 、Reliable メッセージング レスポンダーの要素のシーケンスをそのまま使用し、で応答する必要があります`CreateSequenceResponse`を格納している、`wsrm:Accept`形成相関する 2 つの要素の逆方向シーケンスまたは却下、 `CreateSequence`要求。  
  
- R1104 : 逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。  
  
- R1105 : `AcksTo` の `ReplyTo` エンドポイント参照と `CreateSequence` エンドポイント参照には、オクテット単位で一致するアドレス値が必要です。  
  
     確認します WCF 応答側の URI 部分、`AcksTo`と`ReplyTo`シーケンスを作成する前に Epr は同じです。  
  
- R1106 : `AcksTo` の `ReplyTo` および `CreateSequence` の各エンドポイント参照は、参照パラメーターの同じセットを持つ必要があります。  
  
     WCF は強制されませんが、前提としていますの [参照パラメーター]`AcksTo`と`ReplyTo`で`CreateSequence`は同一で、[参照パラメーターを使用してから`ReplyTo`受信確認と逆方向シーケンス メッセージのエンドポイント参照。  
  
- R1107:使用して 2 つの逆方向シーケンスが確立されたときに、`Offer`メカニズム、`SequenceAcknowledgement`され、アプリケーション メッセージを逆方向シーケンスでフローに送信する必要があります、`ReplyTo`のエンドポイント参照、`CreateSequence`します。  
  
- R1108:Offer 機構を使用して 2 つの逆方向シーケンスが確立されたときに、`[address]`のプロパティ、`wsrm:AcksTo`エンドポイント参照子要素の`wsrm:Accept`の要素、`CreateSequenceResponse`とバイト単位、の送信先URIが一致する必要があります`CreateSequence`.  
  
- R1109:使用して 2 つの逆方向シーケンスが確立されたときに、`Offer`メカニズム、イニシエーターとレスポンダーによるメッセージの受信確認によって送信されたメッセージは、同じエンドポイント参照に送信する必要があります。  
  
     WCF は、Ws-reliable Messaging を使用して、イニシエーターとレスポンダー間で信頼できるセッションを確立します。 WCF の Ws-reliablemessaging 実装は、信頼できるセッション、一方向要求/応答、双方向メッセージング パターン。 Ws-reliable Messaging`Offer`メカニズムで`CreateSequence` / `CreateSequenceResponse` 2 つの相関する逆方向シーケンスを確立することができ、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。 WCF では、セッションのセッションの整合性をエンド ツー エンドの保護などのセキュリティ保証を提供するために、同じパーティを対象としています。 メッセージが同じ送信先に到着したことを確認するは実用的なります。 また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。 そのため、制約 R1104、R1105、および R1108 は、WCF に適用されます。  
  
 `CreateSequence` メッセージの例を次に示します。  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 `CreateSequenceResponse` メッセージの例を次に示します。  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a>シーケンス  
 シーケンスに適用される制約を以下に示します。  
  
- B1201:WCF を生成し、アクセスのシーケンス番号より`xs:long`の最大の包含値 9223372036854775807 します。  
  
- B1202:WCF アクション URI を空の本文の最終メッセージを常に生成するの`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`します。  
  
- B1203:WCF を受信およびを含むシーケンス ヘッダーを含むメッセージを配信する`LastMessage`要素のアクション URI がない限り`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`します。  
  
 シーケンス ヘッダーのサンプル  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a>AckRequested ヘッダー  
 WCF を使用して`AckRequested`keep-alive 機構としてヘッダー。 WCF は、省略可能なは生成されません`MessageNumber`要素。 メッセージを受信すると、`AckRequested`ヘッダーが含まれていますが、`MessageNumber`要素、WCF は無視されます、`MessageNumber`要素の値を次の例に示すようにします。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement ヘッダー  
 WCF では、Ws-reliable Messaging で提供されているシーケンス受信確認の抱き合わせ機構を使用します。  
  
- R1401:使用して 2 つの逆方向シーケンスが確立されたときに、`Offer`メカニズム、`SequenceAcknowledgement`目的の受信者に送信アプリケーション メッセージ ヘッダーを含めることができます。  
  
- B1402:WCF がシーケンス メッセージを受信する前に受信確認を生成する必要があります (を満たすために、例については、`AckRequested`メッセージ)、WCF が生成されます、`SequenceAcknowledgement`の次の例に示すように範囲 0-0 を含むヘッダーをします。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
- B1403:WCF は生成されません`SequenceAcknowledgement`ヘッダーが含まれている、`Nack`要素がサポートする`Nack`要素。  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging エラー  
 Ws-reliablemessaging エラーの WCF 実装に適用される制約の一覧を次には。  
  
- B1501:WCF は生成されません`MessageNumberRollover`エラー。  
  
- B1502:WCF エンドポイントが生成`CreateSequenceRefused`仕様」の説明に従ってフォールトが発生します。  
  
- B1503:When サービス エンドポイントが、接続の制限に達すると、新しい接続を処理できない、WCF を追加生成`CreateSequenceRefused`エラー サブコード`netrm:ConnectionLimitReached`次の例のようにします。  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a>WS-Addressing エラー  
 Ws-reliablemessaging は Ws-addressing で使用するため、WCF Ws-reliable メッセージングの実装は、Ws-addressing エラーを生成できます。 このセクションでは、WCF は、Ws-reliablemessaging レイヤーで明示的に生成する Ws-addressing エラーについて説明します。  
  
- 次のいずれかが true の場合、B1601:WCF は Message Addressing Header Required エラーを生成します。  
  
    - メッセージに `Sequence` ヘッダーと `Action` ヘッダーがない。  
  
    - `CreateSequence` メッセージに `MessageId` ヘッダーがない。  
  
    - `CreateSequence` メッセージに `ReplyTo` ヘッダーがない。  
  
- B1602:WCF が不足しているメッセージに Action Not Supported エラーを生成、`Sequence`ヘッダーであり、`Action`ヘッダーは、Ws-reliable Messaging 仕様で認識されていませんが。  
  
- B1603:WCF をエンドポイントがの検査に基づいて、シーケンスを処理しないことを示す Endpoint Unavailable エラーを生成する、`CreateSequence`メッセージのアドレス指定ヘッダー。  
  
## <a name="protocol-composition"></a>プロトコル コンポジション  
  
### <a name="composition-with-ws-addressing"></a>WS-Addressing によるコンポジション  
 WCF には、Ws-addressing の 2 つのバージョンがサポートされています。Ws-addressing 2004/08 [WS-ADDR] と W3C Ws-addressing 1.0 の推奨事項 [WS ADDR コア] と [WS ADDR SOAP]。  
  
 WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。 WCF に適用される制約の一覧を次には。  
  
- R2101: 両方 Ws-addressing 2004/08 と Ws-addressing 1.0 は、Ws-reliablemessaging で使用できます。  
  
- 指定された Ws-reliablemessaging シーケンス、またはを使用して関連付けられた逆方向シーケンスのペア R2102:A Ws-addressing のバージョンを使用する必要があります、`wsrm:Offer`メカニズム。  
  
### <a name="composition-with-soap"></a>SOAP によるコンポジション  
 WCF では、SOAP 1.1 と Ws-reliablemessaging で SOAP 1.2 の両方の使用をサポートします。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security と WS-SecureConversation によるコンポジション  
 WCF は、Ws-secure Conversation をセキュリティで保護されたトランスポート (HTTPS)、Ws-security によるコンポジション、およびコンポジションを使用して、Ws-reliablemessaging シーケンスを保護を提供します。 WCF に適用される制約の一覧を次には。  
  
- R2301: 個々 のメッセージの整合性だけでなく、Ws-reliablemessaging シーケンスの整合性と機密性を保護する WCF に必要な Ws-secureconversation を使用する必要があります。  
  
- R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。  
  
- R2303:Ws-reliablemessaging シーケンスの有効期間がセッションの有効期間、Ws-secure Conversation を超えた場合、 `SecurityContextToken` Ws-secure Conversation は、対応する Ws-secure Conversation の更新のバインドを使用して更新する必要がありますを使用して確立されます。  
  
- B2304:WS-信頼できるメッセージングのシーケンスまたは相関する逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。  
  
     WCF のソースの生成、`wsse:SecurityTokenReference`の要素拡張セクション内の要素、`CreateSequence`メッセージ。  
  
- R2305:When Ws-secure Conversation を使用して構成を`CreateSequence`メッセージを含める必要があります、`wsse:SecurityTokenReference`要素。  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-ReliableMessaging の WS-Policy アサーション  
 Ws-reliable メッセージングの Ws-policy アサーションを使用する WCF`wsrm:RMAssertion`エンドポイントの機能を記述します。 WCF に適用される制約の一覧を次には。  
  
- B3001:WCF のアタッチ`wsrm:RMAssertion`Ws-policy アサーションを`wsdl:binding`要素。 WCF では、両方の添付ファイルを`wsdl:binding`と`wsdl:port`要素。  
  
- B3002:WCF は、Ws-reliablemessaging アサーションの次の省略可能なプロパティをサポートし、WCF で制御できるを提供します`ReliableMessagingBindingElement`:。  
  
    - `wsrm:InactivityTimeout`  
  
    - `wsrm:AcknowledgementInterval`  
  
     次に例を示します。  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>WS-ReliableMessaging のフロー制御拡張  
 WCF では、Ws-reliable Messaging の機能拡張を使用して、シーケンス メッセージ フローを省略可能なさらに厳密な制御を提供します。  
  
 フロー制御が有効になって、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType>プロパティを`true`します。 WCF に適用される制約の一覧を次には。  
  
- B4001:信頼できるメッセージング フロー制御を有効にすると、WCF が生成されます、`netrm:BufferRemaining`内の要素拡張の要素、`SequenceAcknowledgement`ヘッダー。  
  
- B4002:信頼できるメッセージング フロー制御を有効にすると、WCF は必要ありません、`netrm:BufferRemaining`要素に含まれる`SequenceAcknowledgement`ヘッダー、次の例に示すようにします。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
- B4003:WCF を使用して`netrm:BufferRemaining`を新しいメッセージの数、信頼性の高いメッセージの送信先を示すために入れることができます。  
  
- B4004: 信頼できるメッセージングを WCF サービスは、信頼性の高いメッセージングの送信先アプリケーションが簡単にメッセージを受信できない場合に送信されるメッセージの数を調整します。 信頼できるメッセージングの送信先がメッセージをバッファーに保持する場合、要素の値が 0 になります。  
  
- B4005:WCF が生成されます`netrm:BufferRemaining`整数 0 ~ 4096 の範囲、範囲の値し、0 までの整数値を読み取ると`xs:int`の`maxInclusive`214748364 の値します。  
  
## <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 このセクションでは、Ws-reliable Messaging 別のメッセージ交換パターンを使用すると、WCF の動作が説明します。 各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。  
  
- アドレス不可能なイニシエーター:イニシエーターは; のファイアウォールの内側にレスポンダーは、HTTP 応答でのみイニシエーターにメッセージを配信できます。  
  
- アドレス指定可能なイニシエーター:イニシエーターおよびレスポンダーは HTTP 要求を送信します。つまり、2 つの逆方向の HTTP 接続を確立できます。  
  
### <a name="one-way-non-addressable-initiator"></a>一方向 : アドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF には、1 つの HTTP チャネル経由で 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して RMD から RMS にすべてのメッセージを送信する、RMD し、HTTP 応答に、RMS からのすべてメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`オファーを含まないメッセージです。 WCF のレスポンダーは、`CreateSequence`シーケンスを作成する前にプランがありません。 WCF 応答側に返信すると、`CreateSequence`の要求、`CreateSequenceResponse`メッセージ。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF のイニシエーターを除くすべてのメッセージの返信の受信確認の処理、`CreateSequence`メッセージとエラー メッセージ。 WCF 応答側が常に両方のシーケンスへの応答でスタンドアロンの受信確認を生成し、`AckRequested`メッセージ。  
  
#### <a name="terminatesequence-message"></a>TerminateSequence メッセージ  
 WCF の扱う`TerminateSequence`一方向の操作としては、空の本文と HTTP 202 ステータス コード HTTP 応答の意味が。  
  
### <a name="one-way-addressable-initiator"></a>一方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF には、1 つのシーケンスでは、受信と送信の Http チャネルを使用して、一方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`オファーを含まないメッセージです。 WCF 応答側により、`CreateSequence`シーケンスを作成する前にプランがありません。 WCF 応答側の送信、`CreateSequenceResponse`メッセージは、HTTP 要求で対処するための`ReplyTo`エンドポイント参照。  
  
### <a name="duplex-addressable-initiator"></a>双方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF には、2 つのシーケンスを使用して、受信と送信の HTTP チャネル経由で完全に非同期の双方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`とオファーのメッセージ。 WCF 応答側により、`CreateSequence`シーケンスを作成する前にプランを持ちます。 WCF 送信、`CreateSequenceResponse`をアドレス指定された HTTP 要求で、`CreateSequence`の`ReplyTo`エンドポイント参照。  
  
#### <a name="sequence-lifetime"></a>シーケンスの有効期間  
 2 つのシーケンスは、WCF は、1 つの完全な双方向セッションとして扱います。  
  
 1 つのシーケンスをフォールトするエラーを生成すると WCF には、両方のシーケンスをフォールトするリモート エンドポイントが必要です。 WCF の障害を 1 つのシーケンスをフォールトするエラーを読んだときに両方のシーケンスします。  
  
 WCF は、送信シーケンスを閉じるし、受信シーケンスでのメッセージの処理を続行することができます。 逆に、WCF は、受信シーケンスの終了を処理して、送信シーケンスでメッセージを送信し続けます。  
  
### <a name="request-reply-non-addressable-initiator"></a>要求/応答 : アドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF は、一方向と、要求/応答メッセージ交換のパターンを使用して 2 つのシーケンスの 1 つの HTTP チャネル。 WCF では、HTTP 要求を使用して要求シーケンスのメッセージを送信して、HTTP 応答を使用して応答シーケンスのメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`とオファーのメッセージ。 WCF 応答側により、`CreateSequence`シーケンスを作成する前にプランを持ちます。 WCF 応答側に返信すると、`CreateSequence`の要求、`CreateSequenceResponse`メッセージ。  
  
#### <a name="one-way-message"></a>一方向のメッセージ  
 一方向メッセージ交換のプロトコルを正常に完了するには、WCF のイニシエーターは HTTP 要求で要求シーケンス メッセージを送信し、スタンドアロンの受信`SequenceAcknowledgement`で HTTP 応答メッセージ。 `SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。  
  
 WCF レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードを含む応答で要求に応答できます。  
  
#### <a name="two-way-messages"></a>双方向のメッセージ  
 双方向のメッセージ交換プロトコルを正常に完了するは、WCF イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。 応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。  
  
 WCF 応答側は、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードを含む応答で要求に応答できます。  
  
 一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。  
  
#### <a name="retrying-replies"></a>応答の再試行  
 WCF は、双方向メッセージ交換プロトコルの相関関係の HTTP 要求-応答の相関関係に依存します。 このため、WCF のイニシエーターは停止しませんではなく、HTTP 応答によって、受信確認、ユーザー メッセージ、または障害時に、要求シーケンス メッセージが受信確認されるときに、要求シーケンス メッセージを再試行しています。 WCF 応答側は、応答が関連付けられている要求の HTTP 要求レッグで応答を再試行します。  
  
#### <a name="lastmessage-exchange"></a>LastMessage の交換  
 WCF イニシエーターが生成し、HTTP 要求レッグで空の本文最終メッセージを送信します。 WCF では、応答が必要ですが、実際の応答メッセージは無視されます。 WCF 応答側は、要求シーケンスの空の本文最後のメッセージに応答シーケンスの空の本文最後のメッセージに返信します。  
  
 WCF 応答側アクション URI のない最後のメッセージを受信した場合`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`、最後のメッセージを WCF 添えて応答します。 双方向メッセージ交換プロトコルの場合、最後のメッセージでアプリケーション メッセージが送信されます。一方向メッセージ交換プロトコルの場合、最後のメッセージは空です。  
  
 WCF 応答側では、応答シーケンスの空の本文最後のメッセージの受信確認は必要ありません。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 WCF のイニシエーターが生成し、要求シーケンスを送信するすべての要求が受信されると、有効な応答、 `TerminateSequence` HTTP 要求レッグでメッセージ。 WCF では、応答が必要ですが、実際の応答メッセージは無視されます。 要求シーケンスに返信する WCF 応答側`TerminateSequence`応答シーケンスのメッセージ`TerminateSequence`メッセージ。  
  
 通常のシャットダウン シーケンスでは、両方の `TerminateSequence` メッセージで完全な `SequenceAcknowledgement` を送信します。  
  
### <a name="requestreply-addressable-initiator"></a>要求/応答 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 WCF には、2 つのシーケンスでは、受信と送信の HTTP チャネルを使用して、要求/応答メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`とオファーのメッセージ。 WCF 応答側により、`CreateSequence`シーケンスを作成する前にプランを持ちます。 WCF 送信、`CreateSequenceResponse`をアドレス指定された HTTP 要求で、`CreateSequence`の`ReplyTo`エンドポイント参照。  
  
#### <a name="requestreply-correlation"></a>要求/応答の相関関係  
 WCF イニシエーターにより、すべてのアプリケーション要求メッセージの熊、`MessageId`と`ReplyTo`エンドポイント参照。 WCF のイニシエーターが適用されます、`CreateSequence`メッセージの`ReplyTo`エンドポイント参照を各アプリケーション要求メッセージ。 WCF 応答側では、その着信要求メッセージの熊が必要です、`MessageId`と`ReplyTo`します。 WCF のレスポンダーは、両方のエンドポイント参照の URI を提供する、`CreateSequence`とすべてのアプリケーション要求メッセージは同じです。
