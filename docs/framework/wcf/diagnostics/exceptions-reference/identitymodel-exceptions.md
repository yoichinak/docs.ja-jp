---
title: IdentityModel 例外
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: ee0b5537a415e1ea53c653ae8e8485e94cc713fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998518"
---
# <a name="identitymodel-exceptions"></a>IdentityModel 例外
ここでは、IdentityModel によって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|現在の文字列|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|この引数の値は、この 2 つの型のいずれかである必要があります。|  
|SAMLSubjectNameIdentifierRequiresNameValue|SamlNameIdentifier に対して指定された 'Name' は、NULL や長さ 0 であってはいけません。|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|IssuanceTokenProvider はセキュリティ ネゴシエーションを完了しました。|  
|TraceCodeSecurityNewServerSessionKeyIssued|新しいセキュリティのセッション キーがサーバーによって発行されました。|  
|SAMLAttributeMissingNameAttributeOnRead|読み取り中の SamlAttribute の 'Name' が指定されていないか、長さが 0 です。|  
|UnknownICryptoType|ICrypto 実装はサポートされていません。|  
|TraceCodeSecurityTokenProviderClosed|セキュリティ トークン プロバイダーは閉じられました。|  
|SAMLUnableToLoadAdvice|読み込みに失敗しました、 \<saml:advice > 要素。|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|SamlAuthenticationStatement の読み取り中の 'AuthenticationMethod' 属性は指定されていないか、長さが 0 です。|  
|UnsupportedTransformAlgorithm|サポートされない変換または標準化アルゴリズムです。|  
|SAMLAudienceRestrictionShouldHaveOneAudience|SamlAudienceRestrictionCondition には、少なくとも 1 つの Audience (URI) が含まれている必要があります。|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence は、ID または参照によって少なくとも 1 つの SamlAssertion を参照している必要があります。|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|読み取り中の SamlAudienceRestrictionCondition に 'Audience' 要素の値がありません。|  
|X509ChainBuildFail|指定された X.509 証明書のチェーンを構築できませんでした。 使用された証明書には、検証できない信頼チェーンが含まれています。 証明書を交換するか、certificateValidationMode を変更してください。|  
|XDCannotFindValueInDictionaryString|指定された値 ID が辞書の文字列で見つかりません。|  
|TraceCodeImportSecurityChannelBindingEntry|セキュリティの ImportChannelBinding を開始しています。|  
|PrivateKeyExchangeNotSupported|秘密キーは、交換 KeySpec をサポートしていません。|  
|TokenProviderUnableToGetToken|指定されたトークン プロバイダーはセキュリティ トークンを提供できませんでした。|  
|SAMLEntityCannotBeNullOrEmpty|指定された SamlAssertion エンティティは NULL や空にはできません。|  
|SAMLAssertionRequireOneStatement|SamlAssertion には少なくとも 1 つのステートメントが必要です。 作成する SamlAssertion に少なくとも 1 つの SamlStatement を追加済みであることを確認してください。|  
|AESInvalidInputBlockSize|入力サイズは指定されたバイトの倍数である必要があります。|  
|AESCryptAcquireContextFailed|CSP コンテキストを取得できませんでした。|  
|SAMLAssertionRequireOneStatementOnRead|読み取り中の SamlAssertion に SamlStatement がありませんでした。 SamlAssertion には 1 つ以上の SamlStatement が含まれている必要があります。|  
|TraceCodeSecuritySessionClosedFaultReceived|クライアントのセキュリティ セッションでサーバーからセッション終了済みのフォールトを受信しました。|  
|TraceCodeIssuanceTokenProviderRedirectApplied|IssuanceTokenProvider によってリダイレクト ヘッダーが適用されました。|  
|TraceCodeSecuritySessionClosedFaultSendFailure|セキュリティ セッション終了済みのフォールトをクライアントに送信中にエラーが発生しました。|  
|ValueMustBeZero|この引数の値は 0 である必要があります。|  
|SAMLUnableToResolveSignatureKey|SamlAssertion 署名で見つかった SecurityKeyIdentifier を解決できません。 指定された発行者の SamlAssertion 署名を検証できません。|  
|X509IsNotInTrustedStore|指定された X.509 証明書は信頼されたユーザーのストアにありません。|  
|SAMLElementNotRecognized|指定された要素はサポートされていません。|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|読み取り中の SamlAuthorizationDecisionStatement の 'Resource' 属性は指定されていないか、長さが 0 です。|  
|SamlTokenMissingSignature|SamlAssertion は署名されていません。 SamlAssertions に署名するには、SigningCredentials を設定します。|  
|ExpectedElementMissing|指定された名前空間を持つ予期された要素がありません。|  
|NoKeyIdentifierClauseFound|指定された型の句が SecurityKeyIdentifier で見つかりませんでした。|  
|MissingPrivateKey|X.509 証明書に秘密キーがありません。|  
|UnexpectedEOFFromReader|XML リーダーからの予期しない EOF です。|  
|UnsupportedKeyDerivationAlgorithm|指定されたキー派生アルゴリズムはサポートされていません。|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|指定されたトークンは、指定されたキー識別句の作成をサポートしていません。|  
|LastMessageNumberExceeded|シーケンス番号プロトコル違反が検出されました。|  
|SymmetricKeyLengthTooShort|指定された対称キーの長さが短すぎます。|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|読み取り中の SamlAuthorityBinding に、指定されていないか長さが 0 の 'AuthorityKind' がありました。  これは認められていません。|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer が空です。|  
|InvalidXmlQualifiedName|Xml 修飾名が必要ですが、無効な名前が見つかりました。|  
|SAMLAuthorityKindMissingName|SamlAuthorityBinding の 'AuthorityKind' を表す XmlQualifiedName は、NULL や長さ 0 であってはいけません。|  
|AESCryptEncryptFailed|指定されたデータを暗号化できませんでした。|  
|AuthorizationContextCreated|指定された ID を持つ承認コンテキストが作成されます。|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|SamlSerializer には、SecurityKeyIdentifier を読み取ることができる SecurityTokenSerializer が含まれていません。 カスタム SecurityKeyIdentifier を使用している場合は、カスタムの SecurityTokenSerializer を指定する必要があります。|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|IssuanceTokenProvider によってサービス トークン キャッシュが削減されました。|  
|TraceCodeSecurityTokenProviderOpened|セキュリティ トークン プロバイダーを開きました。|  
|PublicKeyNotRSA|公開キーは RSA キーではありません。|  
|InvalidReaderState|指定された状態は、指定された入力リーダーに対して無効です。|  
|UnableToResolveReferenceUriForSignature|署名の指定された URI を解決してダイジェストを計算できません。|  
|EmptyBase64Attribute|必須の Base64 属性名と名前空間に対して空の値が見つかりました。|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|SAML SubjectConfirmation では、Confirmation Data または KeyInfo が指定されている場合、Confirmation メソッドを指定する必要があります。|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|読み取り中の SamlAudienceRestrictionCondition には 1 つ以上の 'Audience' 値が含まれている必要があります。 この値は見つかりませんでした。|  
|TokenProviderUnableToRenewToken|指定されたトークン プロバイダーは、セキュリティ トークンを更新できませんでした。|  
|AESIVLengthNotSupported|指定されたビットの IV はサポートされていません。 128 ビットの IV のみサポートされます。|  
|SAMLAuthorityBindingMissingAuthorityKind|SamlAuthorityBinding には、NULL でない 'AuthorityKind' が含まれている必要があります。|  
|TraceCodeSecuritySessionDemuxFailure|受信メッセージは既存のセキュリティ セッションの一部ではありません。|  
|TokenRenewalNotSupported|指定されたトークン プロバイダーは、トークンの更新をサポートしていません。|  
|AtLeastOneReferenceRequired|署名には参照が少なくとも 1 つ必要です。|  
|SAMLSignatureAlreadyRead|この署名は既に SAML アサーションに読み込まれています。|  
|AlgorithmAndPrivateKeyMisMatch|指定されたアルゴリズムと秘密キーが適合しません。|  
|EmptyTransformChainNotSupported|空の変換チェーンはサポートされていません。|  
|SspiWrapperEncryptDecryptAssert1|Sspiwrapper::encryptdecrypthelper&#124;'offset' が範囲外です。|  
|SspiWrapperEncryptDecryptAssert2|Sspiwrapper::encryptdecrypthelper&#124;'size' が範囲外です。 SecurityTokenManagerCannotCreateAuthenticatorForRequirement=セキュリティ トークン マネージャーは、指定された要件に対応するトークン認証システムを作成できません。|  
|UnableToCreateKeyedHashAlgorithm|指定された署名アルゴリズムの指定された値から KeyedHashAlgorithm を作成できません。|  
|SAMLUnableToLoadAssertion|\<Saml:assertion > 要素を読み込めませんでした。|  
|X509FindValueMismatchMulti|指定された X509FindType では、引数 findValue の型が 2 つの値のいずれかである必要があります。 引数 findValue は別の型です。|  
|TraceCodeSecurityIdentityDeterminationSuccess|EndpointAddress の ID が特定されました。|  
|UndefinedUseOfPrefixAtElement|この要素で使用される指定されたプレフィックスに定義済みの名前空間がありません。|  
|TraceCodeSecuritySessionResponderOperationFailure|サーバーでセキュリティ セッションの操作に失敗しました。|  
|CannotFindCert|特定の検索条件を使用して X.509 証明書が見つかりません。StoreName、StoreLocation、FindType、FindValue します。|  
|X509InvalidUsageTime|指定された X.509 証明書の使用時間が無効です。 使用時間が、必要な NotBefore の時刻から NotAfter の時刻までの範囲内にありません。|  
|TraceCodeSecurityIdentityDeterminationFailure|EndpointAddress の ID を特定できません。|  
|AsyncObjectAlreadyEnded|End メソッドはこの非同期の結果、オブジェクトで既に呼び出されています。|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|この外部辞書には、必要な文字列の一部の定義しか含まれていません。 指定された文字列はリモート辞書で使用できません。|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|クライアントのセキュリティ セッションはサーバーからキーの更新エラーを受信しました。|  
|SAMLActionNameRequired|SamlAction を表す文字列は、NULL や長さ 0 にはできません。|  
|SignatureVerificationFailed|署名の確認に失敗しました。|  
|TraceCodeSecurityContextTokenCacheFull|SecurityContextSecurityToken のキャッシュがいっぱいです。|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|読み取り中の SamlAssertion の MajorVersion が指定されていないか、長さが 0 です。|  
|SamlAttributeClaimRightShouldBePossessProperty|この SamlAttribute コンストラクターでは、クレームの権限に System.IdentityModel.Claims.Rights.PossessProperty という値が割り当てられていることが要求されます。|  
|AuthorizationPolicyEvaluated|指定された ID を持つポリシーが評価されます。|  
|SAMLUnableToLoadCondtions|\<Saml:conditions > 要素を読み込めませんでした。|  
|AESKeyLengthNotSupported|指定されたビット キーはサポートされていません。 128、192、および 256 ビット キーのみサポートされます。|  
|UserNameCannotBeEmpty|ユーザー名を空にすることはできません。|  
|AlgorithmAndPublicKeyMisMatch|指定されたアルゴリズムと公開キーが適合しません。|  
|SAMLUnableToLoadCondtion|\<Saml:conditions > 要素を読み込めませんでした。|  
|SamlAssertionMissingSigningCredentials|SigningCredentials が SamlAssertion に設定されていません。 SamlAssertions には署名が必要です。続行するには、有効な SigningCredentials を SamlAssertion に設定してください。|  
|SspiPayloadNotEncrypted|バイナリ データは SSPI セキュリティ コンテキストを使用して暗号化されていませんでした。|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|読み取り中の SamlAuthorizationDecisionStatement には SamlAction がありません。|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|セキュリティ プロトコルでは送信メッセージをセキュリティで保護することはできません。|  
|UndefinedUseOfPrefixAtAttribute|指定された属性で使用される指定されたプレフィックスに定義済みの名前空間がありません。|  
|NoInputIsSetForCanonicalization|正規化された出力の書き込みを行うための入力が設定されていません。|  
|TraceCodeSecurityPendingServerSessionAdded|保留中のセキュリティ セッションがサーバーに追加されました。|  
|AsyncCallbackException|AsyncCallback が例外を返しました。|  
|PrivateKeyNotRSA|秘密キーは RSA キーではありません。|  
|TraceCodeSecurityClientSessionKeyRenewed|クライアントのセキュリティ セッションはセッション キーを更新しました。|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|読み取り中の SamlAuthorizationDecisionStatement の 'Decision' は指定されていないか、長さが 0 です。|  
|SAMLAttributeNameAttributeRequired|SamlAttribute に対して指定された 'Name' は、NULL や長さ 0 であってはいけません。|  
|SamlSerializerRequiresExternalSerializers|SamlSerializer は、トークン内に存在する SecurityKeyIdentifier をシリアル化するために SecurityTokenSerializer を必要とします。|  
|UnableToResolveKeyReference|トークン リゾルバーは、指定されたセキュリティ キーの参照を解決できません。|  
|UnsupportedKeyWrapAlgorithm|指定されたキー ラップ アルゴリズムはサポートされていません。|  
|SAMLAssertionMissingIssuerAttributeOnRead|読み取り中の SamlAssertion の 'Issuer' が指定されていないか、長さが 0 です。|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|IssuanceTokenProvider はキャッシュされたサービス トークンを使用しました。|  
|AESCryptGetKeyParamFailed|指定されたキー パラメーターを取得できませんでした。|  
|InvalidNamespaceForEmptyPrefix|この名前空間は空のプレフィックスに対して無効です。|  
|AESCipherModeNotSupported|指定された暗号モードはサポートされていません。 CBC のみがサポートされます。|  
|ArgumentCannotBeEmptyString|引数には空でない文字列を指定する必要があります。|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|読み取り中の SamlAssertion の MinorVersion が指定されていないか、長さが 0 です。|  
|SpecifiedStringNotAvailableInDictionary|指定された文字列は現在の辞書のエントリではありません。|  
|KerberosApReqInvalidOrOutOfMemory|AP-REQ が無効であるか、またはシステムに十分なメモリがありません。|  
|FailLogonUser|指定されたユーザーの LogonUser エラーです。 このユーザーが有効な Windows アカウントを持っていることを確認してください。|  
|ValueMustBeNonNegative|この引数の値は、負ではない値である必要があります。|  
|X509ValidationFail|指定された X.509 証明書の検証に失敗しました。|  
|TraceCodeSecuritySessionRequestorOperationSuccess|セキュリティ セッションの操作がクライアントで正常に完了しました。|  
|SAMLActionNameRequiredOnRead|SamlAction について読み取られる文字列が指定されていないか、長さが 0 です。|  
|KerberosMultilegsNotSupported|ID が UPN として指定されています。 ユーザー アカウントで実行されているサービスを認証するには Kerberos マルチレッグ認証が必要ですが、これはサポートされていません。|  
|SAMLAssertionIdRequired|SamlAssertion の 'assertionId' は、NULL や空であってはいけません。|  
|InvalidOperationForWriterState|指定された操作は、XmlWriter の指定された状態では無効です。|  
|CannotValidateSecurityTokenType|指定されたセキュリティ トークン認証システムは、指定された型のトークンを検証できません。|  
|X509FindValueMismatch|指定された X509FindType では、引数 findValue の型が指定された値である必要があります。 引数 findValue は別の型です。|  
|TraceCodeSecurityClientSessionCloseSent|クライアントのセキュリティ セッションが Close メッセージを送信しました。|  
|SuiteDoesNotAcceptAlgorithm|指定されたアルゴリズムは、指定されたアルゴリズム スイートによる指定された操作には使用できません。|  
|TraceCodeSecuritySessionRequestorOperationFailure|クライアントのセキュリティ セッションの操作が失敗しました。|  
|SAMLUnableToLoadStatement|SamlStatement を読み込むことができませんでした。|  
|InnerReaderMustBeAtElement|内部リーダーは要素に配置されている必要があります。|  
|UnableToCreateTokenReference|セキュリティ トークン参照を作成できません。|  
|TraceCodeSecurityBindingIncomingMessageVerified|セキュリティ プロトコルは受信メッセージを確認しました。|  
|ObjectIsReadOnly|このオブジェクトは読み取り専用です。|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|クライアントのセキュリティ セッションは直前のセッション キーを破棄しました。|  
|SAMLTokenTimeInvalid|SamlToken の有効期限が切れました。 現在の時刻は、トークンの Effective および Expiration 時刻の範囲外です。|  
|TraceCodeSecurityIdentityVerificationSuccess|ID の検査が成功しました。|  
|SigningTokenHasNoKeys|指定された署名トークンにはキーがありません。|  
|TraceCodeSecurityIdentityVerificationFailure|ID の検査が失敗しました。|  
|AESCryptImportKeyFailed|キー マテリアルをインポートできませんでした。|  
|FailInitializeSecurityContext|InitializeSecurityContent エラーです。 サービス プリンシパル名が正しいことを確認してください。|  
|TraceCodeStreamSecurityUpgradeAccepted|ストリームのセキュリティ更新を正常に受信しました。|  
|SAMLAuthorityBindingRequiresLocation|SamlAuthorityBinding で指定された 'Location' 属性は、NULL や長さ 0 であってはいけません。|  
|PublicKeyNotDSA|公開キーは DSA キーではありません。|  
|ImpersonationLevelNotSupported|Kerberos を使用した認証モードは、指定された偽装レベルをサポートしていません。 有効な ID または偽装レベルを指定してください。|  
|RequiredTargetNotSigned|指定された ID を持つ要素には署名が必要ですが、署名されていませんでした。|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|SamlAuthenticationStatement の読み取り中の 'AuthenticationInstant' 属性は指定されていないか、長さが 0 です。|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|読み取り中の SamlEvidence には、SamlAssertion への参照または組み込みの SamlAssertion のどちらもありませんでした。|  
|LengthOfArrayToConvertMustGreaterThanZero|整数に変換する配列の長さは、0 を超える値である必要があります。|  
|InvalidAsyncResult|AsyncResult が無効です。|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|IssuanceTokenProvider は期限切れのサービス トークンを削除しました。|  
|IncorrectUserNameFormat|ユーザー名の形式が無効です。 ユーザー名の形式は、の形式である必要があります"ユーザー名 'または' domain\\\username'。|  
|TraceCodeExportSecurityChannelBindingEntry|セキュリティの ExportChannelBinding を開始しています。|  
|UnsupportedInputTypeForTransform|指定された入力型は変換用にサポートされていません。|  
|CannotFindDocumentRoot|ドキュメントのルートが見つかりません。|  
|XmlBufferQuotaExceeded|XML コンテンツのバッファリングに必要なサイズがバッファー クォータを超過しました。|  
|TraceCodeSecuritySessionClosedResponseSendFailure|セキュリティ セッションの Close 応答をクライアントに送信中、エラーが発生しました。|  
|UnableToResolveReferenceInSamlSignature|AssertionID を持つ SAML 署名の指定された参照を解決できません。|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|SamlSubject では、'NameIdentifier' または 'ConfirmationMethod' を指定する必要があります。 どちらも指定されていません。|  
|SAMLAttributeMissingNamespaceAttributeOnRead|読み取り中の SamlAttribute の 'Namespace' が指定されていないか長さが 0 です。|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|読み取り中の SamlSubjectConfirmation で 'ConfirmationMethod' が見つかりません。|  
|SecurityTokenRequirementHasInvalidTypeForProperty|トークンの要件に、指定されたプロパティの予期されていない型が含まれています。 予期されたプロパティの型は別の値です。|  
|TraceCodeNegotiationTokenProviderAttached|NegotiationTokenProvider が割り当てられました。|  
|TraceCodeSpnegoClientNegotiationCompleted|SpnegoTokenProvider は SSPI ネゴシエーションを完了しました。|  
|SAMLUnableToLoadUnknownElement|選択された SamlSerializer は、この要素を逆シリアル化できません。 カスタム要素のシリアル化を解除するためのカスタム SamlSerializer を登録してください。|  
|CreateSequenceRefused|作成シーケンス要求が RM 宛先により拒否されました。|  
|TraceCodeSecuritySessionRedirectApplied|クライアントのセキュリティ セッションがリダイレクトされました。|  
|SecurityTokenRequirementDoesNotContainProperty|トークンの要件に、指定されたプロパティが含まれていません。|  
|SAMLAttributeValueCannotBeNull|SamlAttribute で見つかった attributeValues の 1 つが NULL 値でした。 SamlAttribute 作成時にリストが NULL でないことを確認してください。|  
|ValueMustBeGreaterThanZero|この引数の値は、正の値である必要があります。|  
|TraceCodeNegotiationAuthenticatorAttached|NegotiationTokenAuthenticator が割り当てられました。|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|SamlAuthorizationDecisionStatement には、少なくとも 1 つの SamlAction が含まれている必要があります。|  
|TraceCodeSecurityTokenAuthenticatorClosed|セキュリティ トークンの認証システムは閉じられました。|  
|TraceCodeSecurityAuditWrittenSuccess|セキュリティ監査ログが正常に書き込まれました。|  
|PrivateKeyNotDSA|秘密キーは DSA キーではありません。|  
|MessageNumberRollover|このシーケンスの最大シーケンス番号を超えました。|  
|AESPaddingModeNotSupported|指定された埋め込みモードはサポートされていません。 PKCS7 および ISO10126 のみサポートされます。|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|読み取り中の SamlSubject について必須の 'NameIdentifier' 要素および 'ConfirmationMethod' 要素が見つかりません。|  
|TraceCodeSecurityAuditWrittenFailure|セキュリティの監査ログへの書き込み時にエラーが発生しました。|  
|UnsupportedCryptoAlgorithm|指定された暗号アルゴリズムは、このコンテキストではサポートされていません。|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|署名トークンに、指定されたアルゴリズム スイートをサポートするキーがありません。|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|読み取り中の SamlNameIdentifier の 'Identifier' 文字列がありません。|  
|SAMLSubjectStatementRequiresSubject|SAML Subject Statement では、SAML サブジェクトを指定する必要があります。|  
|TraceCodeSslClientCertMissing|リモートの SSL クライアントは必要な資格情報を提供できませんでした。|  
|SAMLTokenVersionNotSupported|指定されたメジャー バージョンとマイナー バージョンはサポートされていません。|  
|TraceCodeConfigurationIsReadOnly|構成は読み取り専用です。|  
|TraceCodeSecuritySessionRenewFaultSendFailure|セキュリティ セッション キーの更新エラーをクライアントに送信中にエラーが発生しました。|  
|TraceCodeSecurityInactiveSessionFaulted|アクティブでないセキュリティ セッションはサーバー側でエラーとなりました。|  
|SAMLUnableToLoadAttribute|SamlAttribute を読み込むことができませんでした。|  
|Psha1KeyLengthInvalid|指定された PSHA1 キーの長さが無効です。|  
|KeyIdentifierCannotCreateKey|この SecurityKeyIdentifier には、キーを作成できる句がありません。|  
|X509IsInUntrustedStore|指定された X.509 証明書は、信頼されていない証明書ストアにあります。|  
|UnexpectedXmlChildNode|指定された型の指定された XML 子ノードは、指定された要素に対して予期されていません。|  
|TokenDoesNotMeetKeySizeRequirements|指定されたアルゴリズム スイートのキー サイズ要件が、指定されたトークンによって満たされていません。|  
|TraceCodeSecuritySessionRequestorStartOperation|クライアントでセキュリティ セッションの操作が開始されました。|  
|InvalidHexString|16 進数文字列の形式が無効です。|  
|SamlAttributeClaimResourceShouldBeAString|この SamlAttribute コンストラクターでは、クレームのリソースが 'string' 型であることが要求されます。|  
|SamlSigningTokenNotFound|SamlAssertion は署名されていますが、SamlAssertion に署名したトークンが見つかりません。 SecurityTokenResolver に、SamlAssertion に署名したトークンが含まれていることを確認してください。|  
|TraceCodeSecuritySpnToSidMappingFailure|ServicePrincipalName を SecurityIdentifier にマップできませんでした。|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|指定された非対称暗号から、指定されたアルゴリズムの署名フォーマッタを作成できません。|  
|TraceCodeSecurityServerSessionClosedFaultSent|サーバーのセキュリティ セッションによりセッション終了済みのフォールトがクライアントに送信されました。|  
|UnableToFindPrefix|指定された要素で明示的に使用される指定されたプレフィックスのプレフィックスが見つかりません。|  
|TraceCodeSecurityTokenAuthenticatorOpened|セキュリティ トークンの認証システムを開きました。|  
|RequiredAttributeMissing|指定された属性は指定された要素で必要です。|  
|LocalIdCannotBeEmpty|localId を空にすることはできません。 有効な 'localId' を指定してください。|  
|ValueMustBeInRange|この引数の値は、指定された範囲内である必要があります。|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|IssuanceTokenProvider が新しいセキュリティ ネゴシエーションを開始しました。|  
|InvalidNtMapping|指定された X.509 証明書を Windows アカウントにマップできません。 UPN サブジェクト代替名が必要です。|  
|AESCryptSetKeyParamFailed|指定されたキー パラメーターを設定できませんでした。|  
|TraceCodeSecuritySessionClosedResponseReceived|クライアントのセキュリティ セッションはサーバーから "closed" 応答を受信しました。|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|指定された非対称暗号から、指定されたアルゴリズムの署名デフォーマッタを作成できません。|  
|TraceCodeIdentityModelAsyncCallbackThrewException|非同期コールバックで例外がスローされました。|  
|LengthMustBeGreaterThanZero|この引数の長さは、0 を超える値である必要があります。|  
|FoundMultipleCerts|指定した検索条件を使用して複数の X.509 証明書を参照してください。StoreName, StoreLocation, FindType, FindValue. より具体的な検索条件を指定してください。|  
|AtLeastOneTransformRequired|Transforms 要素には変換が少なくとも 1 つ必要です。|  
|SAMLTokenNotSerialized|SamlAssertion を XML にシリアル化できませんでした。 詳細については、内部例外を参照してください。|  
|TraceCodeSecurityBindingOutgoingMessageSecured|セキュリティ プロトコルは送信メッセージをセキュリティで保護しました。|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|この SecurityKeyIdentifierClause は、キーの作成をサポートしていません。|  
|UnableToResolveTokenReference|トークン リゾルバーは、指定されたトークン参照を解決できません。|  
|UnsupportedEncryptionAlgorithm|指定された暗号化アルゴリズムはサポートされていません。|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|SamlSerializer には、指定された SecurityKeyIdentifier をシリアル化できる SecurityTokenSerializer が含まれていません。 カスタム SecurityKeyIdentifier を使用している場合は、カスタムの SecurityTokenSerializer を指定する必要があります。|  
|SAMLAttributeShouldHaveOneValue|属性値が見つかりませんでした。 SamlAttribute 属性には、少なくとも 1 つの属性値が必要です。|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|セキュリティ プロトコルにより受信メッセージを検証できません。|  
|SamlSigningTokenMissing|SamlSecurityTokenAuthenticator に渡された SamlAssertion に署名トークンがありません。|  
|NoPrivateKeyAvailable|秘密キーがありません。|  
|ValueMustBeOne|この引数の値は 1 でなければなりません。|  
|TraceCodeSecurityPendingServerSessionRemoved|保留中のセキュリティ セッションがサーバーによって有効化されました。|  
|TraceCodeImportSecurityChannelBindingExit|セキュリティの ImportChannelBinding を終了しました。|  
|X509CertStoreLocationNotValid|StoreLocation は、LocalMachine または CurrentUser である必要があります。|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|ライターの設定は、ライターが Start 状態にある場合のみ変更できます。|  
|ArgumentInvalidCertificate|証明書が無効です。|  
|DigestVerificationFailedForReference|指定された参照のダイジェスト認証が失敗しました。|  
|SAMLAuthorityBindingRequiresBinding|SamlAuthorityBinding で指定された 'Binding' 属性は、NULL や長さ 0 であってはいけません。|  
|AESInsufficientOutputBuffer|出力バッファーは指定されたバイトを超える値である必要があります。|  
|SAMLAuthorityBindingMissingBindingOnRead|読み取り中の SamlAuthorityBinding の 'Binding' 属性は指定されていないか、長さが 0 です。|  
|SAMLAuthorityBindingInvalidAuthorityKind|読み取られる SamlAuthorityBinding に無効な AuthorityKind が指定されています。 AuthorityKind の形式は QName である必要があります。|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|Kerberos トークンに指定された NetworkCredentials に有効な UserName がありません。|  
|SSPIPackageNotSupported|指定された SSPI パッケージはサポートされていません。|  
|TokenCancellationNotSupported|指定されたトークン プロバイダーは、トークンのキャンセルをサポートしていません。|  
|UnboundPrefixInQName|バインドされていないプレフィックスが、指定された修飾名で使用されています。|  
|SAMLAuthorizationDecisionResourceRequired|SamlAuthorizationDecisionStatement に指定された 'resource' は、NULL や長さ 0 であってはいけません。|  
|TraceCodeSecurityNegotiationProcessingFailure|サービス セキュリティ ネゴシエーション処理が失敗しました。|  
|SAMLAssertionIssuerRequired|SamlAssertion に対して指定された 'Issuer' は、NULL や空であってはいけません。|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|指定された非対称暗号から、指定されたアルゴリズムの HashAlgorithm を作成できません。|  
|SamlUnableToExtractSubjectKey|SamlSubject で見つかった SecurityKeyIdentifier を SecurityToken に解決できません。 SecurityTokenResolver には、SecurityKeyIdentifier の解決対象となる SecurityToken が含まれている必要があります。|  
|ChildNodeTypeMissing|指定された XML 要素には、指定された型の子がありません。|  
|TraceCodeSecurityPendingServerSessionClosed|保留中のセキュリティ セッションはサーバーによって閉じられました。|  
|TraceCodeSecuritySessionCloseResponseSent|サーバーのセキュリティ セッションはクライアントに Close 応答を送信しました。|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|エンドポイント アドレスの HostName 部分は標準化できません。|  
|FailAcceptSecurityContext|AcceptSecurityContext エラーです。|  
|EmptyXmlElementError|指定された要素を空にすることはできません。|  
|PrefixNotDefinedForNamespace|指定された名前空間のプレフィックスはこのコンテキストで定義されていないため、宣言できません。|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|読み取られる SamlAuthorizationDecisionStatement には複数の Evidence が含まれています。 これは認められていません。|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|SamlSecurityTokenAuthenticator は SamlSecurityToken のみを処理できます。 指定された SecurityTokenType が受信されました。|  
|SAMLAttributeStatementMissingAttributeOnRead|読み取り中の SamlAttributeStatement に 'SamlAttribute' 要素が含まれていません。 これは認められていません。|  
|CouldNotFindNamespaceForPrefix|指定されたプレフィックスの名前空間が見つかりません。|  
|TraceCodeExportSecurityChannelBindingExit|セキュリティの ExportChannelBinding を終了しました。|  
|AESCryptDecryptFailed|指定されたデータを復号化できませんでした。|  
|SAMLAttributeNamespaceAttributeRequired|SamlAttribute に対して指定された 'Namespace' は、NULL や長さ 0 であってはいけません。|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator は SSPI ネゴシエーションを完了しました。|  
|TraceCodeSecurityServerSessionRenewalFaultSent|サーバーのセキュリティ セッションはクライアントにキーの更新エラーを送信しました。|  
|AlgorithmMismatchForTransform|変換用のアルゴリズムで不整合が発生しました。|  
|UserNameAuthenticationFailed|指定された機構を使用したユーザー名/パスワードの認証に失敗しました。 ユーザーは認証されていません。|  
|SamlInvalidSigningToken|SamlAssertion は、プロトコルに従って検証されていないトークンを使用して署名されています。 X.509 証明書を使用している場合は、検証セマンティクスを調べてください。|  
|TraceCodeSecurityServerSessionKeyUpdated|セキュリティ セッション キーはサーバーによって更新されました。|  
|TraceCodeSecurityServerSessionCloseReceived|サーバーのセキュリティ セッションはクライアントから Close メッセージを受信しました。|  
|SAMLAuthenticationStatementMissingSubject|SamlAuthenticationStatement に、必要な SamlSubjectStatement がありません。|  
|UnexpectedEndOfFile|予期しない EOF エラーです。|  
|UnsupportedAlgorithmForCryptoOperation|指定されたアルゴリズムは、指定された操作でサポートされていません。|  
|XmlLangAttributeMissing|必要な xml:lang 属性がありません。|  
|TraceCodeSecurityImpersonationSuccess|サーバー側でセキュリティの偽装が成功しました。|  
|SAMLAuthorityBindingMissingLocationOnRead|読み取り中の SamlAuthorityBinding の 'Location' 属性は指定されていないか、長さが 0 です。|  
|SAMLAttributeStatementMissingSubjectOnRead|SamlAttributeStatement の 'SamlSubject' 要素が指定されていません。|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|読み取り中の SamlAuthorizationDecisionStatement の 'SamlSubject' 要素が指定されていません。|  
|SAMLBadSchema|SamlAssertion の読み取り中に、この指定された要素がスキーマに準拠していないことがわかりました。|  
|SAMLAssertionIDIsInvalid|SamlAssertion の指定された 'assertionId' は、文字または '_' で始まる必要があります。|  
|TraceCodeSecurityActiveServerSessionRemoved|アクティブなセキュリティ セッションはサーバー側で削除されました。|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|指定された対称暗号から、指定されたアルゴリズムの keyedHashAlgorithm を作成できません。|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|SamlAuthenticationStatement に対して指定された 'AuthenticationMethod' は、NULL や長さ 0 であってはいけません。|  
|TraceCodeSecurityImpersonationFailure|サーバー側でセキュリティの偽装が失敗しました。|  
|既定値|(既定)|  
|UnsupportedNodeTypeInReader|指定された名前の指定されたノード型はサポートされていません。|
