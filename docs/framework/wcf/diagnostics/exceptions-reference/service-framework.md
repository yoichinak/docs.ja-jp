---
title: サービス フレームワーク
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 859e718a56ab63c8e012e1851c0730f53cb707be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780758"
---
# <a name="service-framework"></a>サービス フレームワーク
ここでは、サービス フレームワーク データによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|バインディング インスタンスは、指定されたリッスン URI に既に関連付けられています。 2 つのエンドポイントが同じ ListenUniform Resource Indicator を共有する場合、同じバインディング中のオブジェクト インスタンスを共有する必要があります。 2 つの競合するエンドポイントが AddServiceEndpoint() 呼び出しで指定されているか、AddServiceEndpoint() および構成ファイルの両方に指定されています。|  
|AChannelServiceEndpointIsNull0|チャネルまたはサービスのエンドポイントが NULL です。|  
|AChannelServiceEndpointSContractSNameIsNull0|チャネルまたはサービスのエンドポイントのコントラクト名が NULL または空です。|  
|AChannelServiceEndpointSContractSNamespace0|チャネルまたはサービスのエンドポイントの名前空間が NULL です。|  
|BaseAddressCannotHaveFragment|ベース アドレスに URI フラグメントを含めることはできません。|  
|BaseAddressCannotHaveQuery|ベース アドレスに URI クエリ文字列を含めることはできません。|  
|BaseAddressCannotHaveUserInfo|ベース アドレスに URI ユーザー情報セクションを含めることはできません。|  
|BaseAddressDuplicateScheme|このコレクションには、指定されたスキームを使用するアドレスが既に含まれています。 このコレクションでは、スキームごとに 1 つのアドレスしか許可されていません。|  
|BaseAddressMustBeAbsolute|ベース アドレスとして使用できる絶対 URI は 1 つのみです。|  
|BindingDoesnTSupportAnyChannelTypes1|指定されたバインディングは、どのチャネルの種類の作成もサポートしていません。 カスタム バインド内のバインド要素が適切にスタックされていないか、スタックの順序が間違っています。 スタックの一番下にはトランスポートが必要です。 バインド要素の推奨順序は次のとおりです。TransactionFlow、ReliableSession、Security、CompositeDuplex、OneWay、StreamSecurity、MessageEncoding、次のように転送します。|  
|BindingDoesnTSupportDuplexButContractRequires1|コントラクトには Duplex が必要です。 指定されたバインディングはこれをサポートしていないか、サポートするように正しく構成されていません。|  
|BindingDoesnTSupportOneWayButContractRequires1|コントラクトには OneWay が必要です。 指定されたバインディングはこれをサポートしていないか、サポートするように正しく構成されていません。|  
|BindingDoesnTSupportRequestReplyButContract1|コントラクトには Request/Reply が必要です。 指定されたバインディングはこれをサポートしていないか、サポートするように正しく構成されていません。|  
|BindingDoesnTSupportSessionButContractRequires1|コントラクトには Session が必要です。  指定されたバインディングはこれをサポートしていないか、サポートするように正しく構成されていません。|  
|BindingDoesnTSupportTwoWayButContractRequires1|コントラクトは、TwoWay (要求-応答、または双方向) を必要とします。 指定されたバインディングはこれをサポートしていないか、サポートするように正しく構成されていません。|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|DeliveryRequirementsAttribute は QueuedDelivery を許可していません。 指定されたコントラクトを持つエンドポイントのバインディングはこれをサポートしています。|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|DeliveryRequirementsAttribute には QueuedDelivery が必要です。 指定されたコントラクトを持つエンドポイントのバインディングはこれをサポートしていないか、サポートするように正しく構成されていません。|  
|channelDoesNotHaveADuplexSession0|現在のチャネルは、出力セッションの終了をサポートしていません。 このチャネルは、ISessionChannel を実装していません\<IDuplexSession >。|  
|ClientRuntimeRequiresFormatter0|SerializeRequest と DeserializeReply の両方が false ではないため、指定された ClientOperation にはフォーマッタが必要です。|  
|CommunicationObjectAborted1|指定された通信オブジェクトは停止しているため、通信に使用できません。|  
|CommunicationObjectAbortedStack2|指定された通信オブジェクトは、停止しているため、通信に使用できません。 {1}|  
|CommunicationObjectBaseClassMethodNotCalled|指定された通信オブジェクトが仮想関数をオーバーライド{1}しますが、基底クラスで定義されているバージョンを呼び出しません。|  
|ContractIsNotSelfConsistentItHasOneOrMore2|指定されたコントラクトには、IsTerminating 操作または IsInitiating 以外の操作が 1 つ以上あります。 SessionMode.Required に設定された SessionMode プロパティがありません。 IsInitiating 属性と IsTerminating 属性は、セッションのコンテキストでのみ使用できます。|  
|CouldnTCreateChannelForChannelType2|指定されたチャネルの種類が要求されましたが、指定されたバインディングはこれをサポートしていないか、サポートするように正しく構成されていません。|  
|DispatchRuntimeRequiresFormatter0|DeserializeRequest と SerializeReply の両方が false ではないため、指定された DispatchOperation にはフォーマッタが必要です。|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|IAsyncResult デザイン パターンを使用する場合、OperationContractAttribute と共に End メソッドを使用することはできません。 OperationContractAttribute と共に使用できるのは、対応する Begin メソッドのみです。 この属性は、メソッドの Begin と End のペアに適用されます。|  
|EndpointListenerRequirementsCannotBeMetBy3|指定されたバインディングの IChannelListener が ChannelDispatcher の要件を満たすことができません。コントラクトには、指定されたこれらのチャネルの種類のいずれか 1 つのサポートが必要ですが、 バインディングがサポートしているのは、指定されたこれらのチャネルの種類のみです。|  
|EndpointsMustHaveAValidBinding0|エンドポイントには有効なバインディングが必要です。|  
|InvalidOrUnrecognizedAction|指定されたアクションが無効であるか、または認識できないため、メッセージを処理できません。|  
|MultipleMebesInParameters|BindingContext の BindingParameter に複数の MessageEncodingBindingElement が見つかりました。 CustomBinding に複数の MessageEncodingBindingElement を含めることはできません。 これらの要素の 1 つ以外はすべて削除します。|  
|MultipleStreamUpgradeProvidersInParameters|BindingContext の BindingParameter に複数の IStreamUpgradeProviderElement が見つかりました。 CustomBinding に複数の IStreamUpgradeProviderElement を含めることはできません。 これらの要素の 1 つ以外はすべて削除します。|  
|NoChannelBuilderAvailable|バインディングに TransportBindingElement が含まれていないため、このバインディングを使用してチャネル ファクトリやチャネル リスナーを作成することはできません。 いずれのバインディングにも TransportBindingElement から派生するバインド要素を少なくとも 1 つ含んでいる必要があります。|  
|NotAllBindingElementsBuilt|このバインディング内の一部のバインド要素は、チャネル ファクトリ/チャネル リスナーの構築時に使用されませんでした。 バインド要素の順序が正しくありません。 バインド要素の推奨順序は次のとおりです。TransactionFlow、ReliableSession、Security、CompositeDuplex、OneWay、StreamSecurity、MessageEncoding、次のように転送します。  TransportBindingElement は最後である必要があります。 指定されたバインド要素は構築されませんでした。|  
|RuntimeRequiresInvoker0|ディスパッチ操作は呼び出しの起動者が必要です。|  
|ServiceHasZeroAppEndpoints|指定されたサービスには、アプリケーション (インフラストラクチャ以外) エンドポイントがありません。 これは、アプリケーション用の構成ファイルが見つからなかったこと、サービス名と一致するサービス要素が構成ファイル内から見つからなかったこと、またはサービス要素内でエンドポイントが定義されていないことが原因である可能性があります。|  
|SFxActionMismatch|動作が一致しないため、入力されたメッセージを作成できません。 指定されたアクションを予期していましたが、別のアクションが発生しました|  
|SFxAnonymousTypeNotSupported|指定されたメッセージの指定された部分は種類が不明であるため、RPC でのエクスポートやエンコードを実行できません。|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|構成ファイルの serviceMetadata セクションにある ExternalMetadataLocation プロパティまたは externalMetadataLocation 属性を介して ServiceMetadataBehavior に渡された URL は、相対 URL であったため、この URL を解決するためのベース アドレスがありません。|  
|SFxBadMetadataMustBePolicy|ポリシーでは、指定された名前空間と名前を持つ XmlElement を指定する必要があります。 この XmlElement は、指定された名前空間と名前を持ちます。|  
|SFxBodyObjectTypeCannotBeInherited|RPC スタイルの body オブジェクトとして使用されるオブジェクト以外のクラスから、指定された型を継承することはできません。|  
|SFxBodyObjectTypeCannotBeInterface|指定された型が実装している指定されたインターフェイスは、RPC スタイルの body オブジェクトでサポートされていません。|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|CallbackBehaviorAttribute は、双方向コントラクトを使用したエンドポイント上の操作としてのみ実行できます。 指定されたコントラクトは、コールバック操作を含んでいないため、双方向ではありません。|  
|SFxCallbackRequestReplyInOrder1|現在のメッセージが処理を完了するまで、この操作から応答を受信することはできません。 順番を無視したメッセージ処理を許可するには、指定された対象で Reentrant または Multiple の ConcurrencyMode を指定してください。|  
|SfxCallbackTypeCannotBeNull|指定されたコントラクトを DuplexChannelFactory と共に使用するには、このコントラクトで有効なコールバック コントラクトを指定する必要があります。 使用しているコントラクトにコールバック コントラクトがある場合は、DuplexChannelFactory の代わりに ChannelFactory を使用してください。|  
|SFxCannotGetMetadataFromLocation|MetadataExchangeClient は HTTP および HTTPS の MetadataLocations からのみメタデータを取得できます。 指定された対象からメタデータを取得できません。|  
|SFxCannotHttpGetMetadataFromAddress|MetadataExchangeClient は、MetadataExchangeClientMode HttpGet を使用した場合に HTTP アドレスまたは HTTPS アドレスからのみメタデータを取得できます。 指定された対象からメタデータを取得できません。|  
|SFxCannotImportAsParameters_Bare|指定された操作は RPC でもラップされたドキュメントでもないため、メッセージ コントラクトを生成しています。|  
|SFxCannotImportAsParameters_DifferentWrapperName|指定されたメッセージのラッパーの名前が既定値と一致しないため、メッセージ コントラクトを生成しています。|  
|SFxCannotImportAsParameters_DifferentWrapperNs|指定されたメッセージのラッパーの名前空間が既定値と一致しないため、メッセージ コントラクトを生成しています。|  
|SFxCannotImportAsParameters_ElementIsNotNillable|指定された名前空間の指定された要素名が nillable に設定されていないため、メッセージ コントラクトを生成しています。|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|指定されたメッセージにヘッダーが含まれるため、メッセージ コントラクトを生成しています。|  
|SFxCannotImportAsParameters_Message|指定された操作には、引数または戻り値の型として型指定されていない Message が含まれるため、メッセージ コントラクトを生成しています。|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|指定されたメッセージには保護が必要なため、メッセージ コントラクトを生成しています。|  
|SFxCannotImportAsParameters_NamespaceMismatch|指定されたメッセージ部分の名前空間が既定値と一致しないため、メッセージ コントラクトを生成しています。|  
|SFxCannotRequireBothSessionAndDatagram3|指定されたコントラクトは SessionMode.NotAllowed を指定し、かつ SessionMode.Required を指定しています。 どちらかの SessionMode の値を変更するか、エンドポイントごとに異なるアドレス (または ListenURI) を指定してください。|  
|SFxCannotSetExtensionsByIndex|このコレクションは、インデックスによる拡張の設定をサポートしていません。 InsertItem または RemoveItem メソッドを使用してください。|  
|SFxChannelDispatcherDifferentHost0|この ChannelDispatcher は、指定された ServiceHost に現在アタッチされていません。|  
|SFxChannelDispatcherMultipleHost0|複数の ServiceHost に ChannelDispatcher を追加することはできません。|  
|SFxChannelDispatcherNoHost0|ChannelDispatcher は、ServiceHost にアタッチされていないため、開くことができません。|  
|SfxChannelFactoryDisposed|この ChannelFactory は既に破棄されているため開けません。 この ChannelFactory を使用する前に再作成してください。|  
|SFxChannelFactoryNoBinding|ChannelFactory のエンドポイントにバインディングが関連付けられていないため、ChannelFactory を開くことができません。 コンストラクターまたはエンドポイント プロパティでバインディングを指定してください。|  
|SFxChannelTerminated0|IsTerminating が設定された操作はこのチャネルで既に呼び出されており、その結果このチャネルの接続は終了しました。 このチャネルでは追加の操作を呼び出すことはできません。 通信を続行するには、このチャネルを再作成してください。|  
|SFxCloseTimedOut1|ServiceHost の閉じる操作が、指定された時間後に中止されました。 クライアントがセッションフル チャネルを要求された時間内に閉じることができなかったことが原因である可能性があります。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|  
|SfxCloseTimedOutWaitingForDispatchToComplete|サービスのディスパッチが完了するのを待機しているときに Close プロセスがタイムアウトしました。|  
|SFxCodeGenIsNotAssignableFrom|指定された対象を割り当てることはできません。|  
|SFxConfigChannelConfigurationNotFound|ServiceModel クライアント構成セクションで、指定された名前とコントラクトを持つエンドポイント要素が見つかりません。|  
|SFxConflictingGlobalElement|指定された名前空間に含まれる指定された名前を持つトップ レベルの XML 要素が、指定された型を参照できません。 この要素は別の型を既に参照しています。 異なる操作名を使用するか、MessageBodyAttribute を使用して、メッセージまたはメッセージ部分に別の名前を指定してください。|  
|SFxContractHasZeroInitiatingOperations|コントラクトには、少なくとも 1 つの IsInitiating=true 操作が必要です。|  
|SFxContractHasZeroOperations|コントラクトには、少なくとも 1 つの操作が必要です。|  
|SFxContractInheritanceRequiresInterfaces|指定された型のサービス クラスでは、ServiceContract が定義されていると共に、指定された型から ServiceContract を継承しています。 コントラクトの継承はインターフェイス型の中でのみ使用できます。 クラスに ServiceContractAttribute が設定されている場合、そのクラスは、ServiceContractAttribute が設定された階層内の唯一の型である必要があります。  指定された型の ServiceContractAttribute を、指定された型で実装されている別のインターフェイスに移動してください。|  
|SFxCreateDuplexChannel1|指定されたコントラクトのコールバック コントラクトは存在していないか、またはどの操作も定義していません。 これが双方向コントラクトでない場合は、DuplexChannelFactory の代わりに ChannelFactory を使用してください。|  
|SFxCreateDuplexChannelNoCallback|この CreateChannel オーバーロードは DuplexChannelFactory のこのインスタンスでは呼び出せません。 DuplexChannelFactory が InstanceContext を使用して初期化されませんでした。 InstanceContext を受け取る CreateChannel オーバーロードを呼び出します。|  
|SFxCreateDuplexChannelNoCallback1|この CreateChannel オーバーロードは DuplexChannelFactory のこのインスタンスでは呼び出せません。 Type を使用して DuplexChannelFactory が初期化されて、有効な InstanceContext が指定されませんでした。 InstanceContext を受け取る CreateChannel オーバーロードを呼び出します。|  
|SFxCreateDuplexChannelNoCallbackUserObject|この CreateChannel オーバーロードは DuplexChannelFactory のこのインスタンスでは呼び出せません。 DuplexChannelFactory に渡された InstanceContext に有効な UserObject が含まれていません。|  
|SFxCreateNonDuplexChannel1|ChannelFactory は指定されたコントラクトをサポートしていません。 ChannelFactory は 1 つ以上の操作が含まれたコールバック コントラクトを定義しています。 ChannelFactory の代わりに DuplexChannelFactory を使用してください。|  
|SFxCustomBindingNeedsTransport1|指定されたコントラクトを持つ ServiceEndpoint の CustomBinding には、TransportBindingElement がありません。 いずれのバインディングにも TransportBindingElement から派生するバインド要素を少なくとも 1 つ含んでいる必要があります。|  
|SFxCustomBindingWithoutTransport|このカスタム バインドには TransportBindingElement がないため、このバインディング用のスキームを計算できません。 いずれのバインディングにも TransportBindingElement から派生するバインド要素を少なくとも 1 つ含んでいる必要があります。|  
|SFxDataContractSerializerDoesNotSupportBareArray|DataContractSerializer は、指定された要素で指定されたコレクションをサポートしていません。|  
|SFxDictionaryIsEmpty|辞書が空なので、この操作を行えません。|  
|SFxDocEncodedNotSupported|指定された対象の反映中にエラーが発生しました。 エンコードされたドキュメントはサポートされていません。 'Use' をリテラルに変更するか、'Style' を RPC に変更してください。|  
|SFxDuplicateInitiatingActionAtSameVia|このサービスには、指定された対象でリッスンしているエンドポイントが複数あります。 これらのエンドポイントでは、指定された開始アクションが同じです。 ディスパッチャーがメッセージ処理用の正しいエンドポイントを判断できなくなるため、このアクションが指定されたメッセージは削除されます。|  
|SFXEndpointBehaviorUsedOnWrongSide|指定された IEndpointBehavior をサーバーで使用することはできません。 この動作はクライアントにのみ適用できます。|  
|SFxEndpointNoMatchingScheme|指定されたバインディングを使用するエンドポイントの、指定されたスキームに適合するベース アドレスが見つかりません。 登録されているベース アドレス スキームが指定されています。|  
|SFxErrorCreatingMtomReader|MTOM メッセージ用のリーダーを作成しているときにエラーが発生しました。|  
|SFxErrorDeserializingFault|サーバーから無効な SOAP フォールトが返されました。 詳細については、InnerException を参照してください。|  
|SFxErrorDeserializingHeader|指定されたメッセージに含まれるヘッダーの 1 つの逆シリアル化中にエラーが発生しました。 詳細については、InnerException を参照してください。|  
|SFxErrorReflectingOnMethod3|指定された型で、指定されたメソッドの指定された属性の読み込み中にエラーが発生しました。  詳細については、InnerException を参照してください。|  
|SFxErrorReflectingOnParameter4|指定された型の指定されたメソッドの指定されたパラメーターの指定された属性を読み込み中にエラーが発生しました。 詳細については、InnerException を参照してください。|  
|SFxErrorReflectingOnType2|指定された型の指定された属性を読み込み中にエラーが発生しました。  詳細については、InnerException を参照してください。|  
|SFxErrorSerializingBody|指定されたメッセージの本文のシリアル化中にエラーが発生しました。 詳細については、InnerException を参照してください。|  
|SFxErrorSerializingHeader|指定されたメッセージに含まれるヘッダーの 1 つのシリアル化中にエラーが発生しました。 詳細については、InnerException を参照してください。|  
|SFxExpectedIMethodCallMessage|内部エラーです。 メッセージは有効な IMethodCallMessage である必要があります。|  
|SFxExportMustHaveType|指定された操作の指定された部分には有効な CLR 型が含まれていないため、エクスポートできません。|  
|SFxHeaderNotUnderstood|メッセージは処理されませんでした。 指定された名前空間の指定されたヘッダーをこのメッセージの受信側で認識できませんでした。 このエラーは一般に、受信側で処理できない通信プロトコルがこのメッセージの送信側で有効になっていることを示します。 クライアントのバインディングの構成がサービスのバインディングと一致していることを確認してください。|  
|SFxHeadersAreNotSupportedInEncoded|指定されたメッセージに、リモート プロシージャ コールでエンコードされたスタイルで使用するヘッダーを含めることはできません。|  
|SFxInconsistentWsdlOperationStyleInMessageParts|指定された操作内のメッセージを構成するすべての部分は、型または要素のいずれかを格納している必要があります。|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|指定された操作内のメッセージから生成された指定されたスタイルが、バインディングによって指定された予期された指定のスタイルと一致しません。|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult が指定されていないか、型が正しくありません。|  
|SFxInvalidMessageBody|OperationFormatter で、無効なメッセージ本文が検出されました。 指定された名前と名前空間を持つ 'Element' ノード型が予期されていましたが、 指定された名前と名前空間を持つ指定されたノード型が見つかりました。|  
|SFxInvalidMessageBodyEmptyMessage|OperationFormatter は、メッセージが空のため、メッセージから情報を逆シリアル化できません。|  
|SFxInvalidMessageBodyErrorDeserializingParameter|指定されたパラメーターを逆シリアル化しようとしているときにエラーが発生しました。 詳細については InnerException を参照してください。|  
|SFxInvalidMessageBodyErrorSerializingParameter|指定されたパラメーターをシリアル化しようとしているときにエラーが発生しました。 InnerException メッセージが指定されています。  詳細については、InnerException を参照してください。|  
|SFxInvalidMessageBodyUnexpectedNode|パラメーターを逆シリアル化中に、指定された名前空間から指定された予期しないノードが検出されました。|  
|SFxInvalidMessageContractSignature|指定された操作に、MessageContractAttribute が設定されたパラメーターまたは戻り値の型が含まれています。 メッセージ コントラクトを使用して要求メッセージを表現するには、この操作には MessageContractAttribute を持つ単一のパラメーターが含まれている必要があります。 メッセージ コントラクトを使用して応答メッセージを表現するには、この操作の戻り値は MessageContractAttribute を持つ型である必要があります。 この操作には 'out' パラメーターや 'ref' パラメーターを含めることはできません。|  
|SFxInvalidReplyAction|操作の送信応答メッセージには指定された Action が含まれていますが、この操作のコントラクトは別の ReplyAction を指定しています。 メッセージで指定された Action がコントラクト内の ReplyAction と一致しているか、この操作のコントラクトが ReplyAction='*' を指定している必要があります。|  
|SFxInvalidRequestAction|操作の送信要求メッセージには指定された Action が含まれていますが、この操作のコントラクトは別の RequestAction を指定しています。 メッセージで指定された Action がコントラクト内の RequestAction と一致しているか、操作コントラクトが RequestAction='*' を指定している必要があります。|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|指定されたコントラクトはコールバック コントラクトを定義しているため、このコントラクトでは静的な CreateChannel メソッドを使用できません。 DuplexChannelFactory に静的な CreateChannel オーバー ロードのいずれかを使用して、\<TChannel >。|  
|SFxInvalidStreamInRequest|指定された操作における要求をストリームにするには、この操作は Stream 型の単一のパラメーターを持つ必要があります。|  
|SFxInvalidStreamInResponse|指定された操作における応答をストリームにするには、この操作が Stream 型の単一の out パラメーターまたは戻り値を持つ必要があります。|  
|SFxInvalidStreamInTypedMessage|メッセージ コントラクト プログラミング モデルでストリームを使用するには、指定された型が Stream 型の単一の MessageBody メンバーを持つ必要があります。|  
|SFxInvalidUseOfPrimitiveOperationFormatter|PrimitiveOperationFormatter に、サポートされていないパラメーターまたは戻り値の型が指定されました。|  
|SFxMessageContractBaseTypeNotValid|指定された型は MessageContract を定義していますが、その派生元である指定された型は MessageContract を定義していません。 指定された継承階層内のすべてのオブジェクトが MessageContract を定義している必要があります。|  
|SFxMethodNotSupported1|指定されたメソッドは、このオブジェクトでサポートされていません。 これは、メソッドが OperationContractAttribute でマークされていない場合、またはインターフェイスの種類が ServiceContractAttribute でマークされていない場合に発生することがあります。|  
|SFxMethodNotSupportedByType2|ServiceHost の指定された実装型は、指定されたサービス コントラクトを実装していません。|  
|SFxMethodNotSupportedOnCallback1|指定されたコールバック メソッドはサポートされていません。 この原因としては、このメソッドに OperationContractAttribute が設定されていないこと、またはそのインターフェイスの型が ServiceContractAttribute の CallbackContract のターゲットでないことが考えられます。|  
|SFxMismatchedOperationParent|DispatchOperation または ClientOperation を追加できるのは、親の DispatchRuntime または ClientRuntime だけです。|  
|SFxNameCannotBeEmpty|Name プロパティを空の文字列にすることはできません。|  
|SfxNoTypeSpecifiedForParameter|パラメーターに CLR 型が指定されていなかったため、操作を生成できませんでした。|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute を指定できるのはサービス クラスのみです。 ServiceContract インターフェイスで指定することはできません。 指定された型の指定されたメソッドは、これに違反しています。|  
|SFxOperationContractOnNonServiceContract|指定されたメソッドには OperationContractAttribute が設定されていますが、それを囲む指定された型に ServiceContractAttribute が設定されていません。 OperationContractAttribute は、ServiceContractAttribute 型のメソッド、または CallbackContract 型でのみ使用できます。|  
|SFxParameterCountMismatch|指定された引数の数と必要な引数の数が一致しませんでした。 具体的には、指定された引数には指定された個数の要素があり、必要な引数には指定された個数の要素があります。|  
|SFxPartNameMustBeUniqueInRpc|リモート プロシージャ コール メッセージ内で、指定されたメッセージ部分名が一意ではありません。|  
|SFxReplyActionMismatch3|指定されたアクションが含まれる指定された操作に対する応答メッセージを受信しましたが、 クライアント コードには指定されたアクションが必要です。|  
|SFxRequestReplyNone|"None" アドレスを対象にした WS-Addressing の ReplyTo または FaultTo ヘッダーが含まれたメッセージを受信しました。 これらの値は、要求-応答の操作に対しては無効です。 ReplyTo または FaultTo の値として "None" をサポートする必要がある場合は、一方向の操作を使用するか、ManualAddressing を有効にしてください。|  
|SFxRequestTimedOut1|この要求操作は、指定された構成済みの時間内に応答を受信しませんでした。 許可された時間はより長く設定されたタイムアウトの一部になる可能性があります。 この原因としては、サービスがまだこの操作を処理していること、またはサービスが応答メッセージを送信できなかったことが考えられます。|  
|SFxRequestTimedOut2|指定された場所に送信されたこの要求操作は、指定された構成済みの時間内に応答を受信しませんでした。 許可された時間はより長く設定されたタイムアウトの一部になる可能性があります。 この原因としては、サービスがまだこの操作を処理していること、またはサービスが応答メッセージを送信できなかったことが考えられます。|  
|SFxSchemaDoesNotContainType|指定されたターゲット名前空間を持つスキーマに、指定された名前を持つ型が含まれていません。|  
|SfxServiceContractAttributeNotFound|指定されたコントラクト型には ServiceContractAttribute 属性が設定されていません。 有効なコントラクトを定義するには、指定された型に ServiceContractAttribute が設定されている必要があります。 コントラクト インターフェイスまたはサービス クラスを型として指定できます。|  
|SFxServiceContractGeneratorConfigRequired|GenerateServiceEndpoint メソッドを使用して構成情報を生成するためには、有効な構成オブジェクトを使用して ServiceContractGenerator インスタンスが初期化されている必要があります。|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|ServiceHost が次のいずれかの状態になった後に、エンドポイントを追加することはできません。<br /><br /> 開かれました。<br />障害<br />終わる<br />クローズ|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Description プロパティが初期化される前に、エンドポイントを追加することはできません。|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|ServiceMetadataBehavior の HttpGetEnabled プロパティが True に設定され、HttpGetUrl プロパティが相対アドレスですが、HTTP ベース アドレスがありません。 HTTP ベース アドレスを指定するか、HttpGetUrl を絶対アドレスに設定してください。|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|ServiceMetadataBehavior の HttpsGetEnabled プロパティが True に設定され、HttpsGetUrl プロパティが相対アドレスですが、HTTPS ベース アドレスがありません。 HTTPS ベース アドレスを指定するか、HttpsGetUrl を絶対アドレスに設定してください。|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|動作 URI は、指定されたスキームの相対 URI または絶対 URI である必要があります。 指定された URI は、指定されたスキームの絶対 URI です。|  
|SFxStreamRequestMessageClosed|このストリームを含むメッセージは閉じられています。 サービス操作が返った後に要求ストリームにアクセスすることはできません。|  
|SFxStreamResponseMessageClosed|このストリームを含むメッセージは閉じられています。|  
|SFxTerminateRequestProcessingException|操作パイプラインを拡張する場合、このメッセージの処理を中止する必要があります。|  
|SFxTerminatingOperationAlreadyCalled1|IsTerminating 操作が既に呼び出されているため、このチャネルでこれ以上、メッセージを送信することはできません。|  
|SFxThrottleLimitMustBeGreaterThanZero0|スロットル制限は、0 より大きい必要があります。 スロットル制限を無効にするには、値を Int32.MaxValue に設定してください。|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|RPC エンコード スタイルを使用しているときに、操作にパラメーターがない場合や void の戻り値がある場合は、メッセージ コントラクト型や System.ServiceModel.Channels.Message 型を使用できません。 ブランク メッセージ コントラクト型を指定された操作に、パラメーターまたは戻り値の型として追加してください。|  
|SFxUserCodeThrewException|指定されたユーザー操作によって、ユーザー コードで未処理の例外がスローされました。 この問題が繰り返し発生する場合は、指定されたメソッドの実装にエラーが含まれている可能性があります。|  
|SfxUseTypedMessageForCustomAttributes|指定されたパラメーターには追加属性が必要であるため、このパラメーターを操作パラメーターにマップすることはできません。|  
|SFxVersionMismatchInOperationContextAndMessage2|OperationContext.Current の MessageVersion が、処理中のメッセージのヘッダー バージョンと一致しないため、送信ヘッダーをメッセージに追加できません。|  
|SFxWellKnownNonSingleton0|サービス インスタンスを受け取る ServiceHost コンストラクターのいずれか 1 つを使用するには、サービスの InstanceContextMode が InstanceContextMode.Single に設定されている必要があります。 これは ServiceBehaviorAttribute を使用して構成できます。 または、型引数を受け取る ServiceHost コンストラクターを使用してください。|  
|SFxWrapperTypeHasMultipleNamespaces|指定されたメッセージのラッパー型は複数の名前空間を持つため、データ コントラクト型として投影できません。 XmlSerializer を使用してください。|  
|UriMustBeAbsolute|URI は絶対 URI である必要があります。|
