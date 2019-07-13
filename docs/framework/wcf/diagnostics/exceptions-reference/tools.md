---
title: ツール
ms.date: 03/30/2017
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
ms.openlocfilehash: 6c4ada74c2fc6aba84eb1fe46f4d7cdee9978d13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780745"
---
# <a name="tools"></a>ツール
このトピックでは、Windows Communication Foundation (WCF) ツールによって生成されるすべての例外を使用します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|ParametersTarget|\<enum>|  
|ParametersToolConfig|\<configFile>|  
|ErrInvalidPath|指定されたパスが無効です。 指定された引数を確認してください。|  
|ParametersReference|\<ファイルのパス >|  
|WrnCannotLoadConfigFileForValidation|指定された場所から読み込んだ構成ファイルの処理中にエラーが発生しました。 この構成ファイルで定義されているサービスを検証できません。|  
|MoreHelp|詳細なヘルプを表示するには、指定された引数と共に "svcutil" を入力してください。|  
|HelpMergeConfig|既存ファイルを上書きする代わりに、生成された構成が既存ファイルにマージされます。|  
|ErrCannotWriteFile|出力ファイルに書き込めません。|  
|ErrInvalidNamespaceArgument|指定された無効な値が指定されたオプションに渡されました。 コンマ区切りのターゲット名前空間と CLR 名前空間の組み合わせを指定してください。|  
|HelpImportXmlType|非 DataContract 型を IXmlSerializable 型としてインポートするように DataContract シリアライザーを構成します。|  
|ErrExclusiveOptionsSpecified|もう一方の指定されたオプションが指定されているときは、指定されたオプションを使用できません。|  
|WrnHttpGetFailed|指定された URI で HTTP GET Error が発生しました。|  
|ErrInputFileNotAssemblyOrMetadata|指定された入力引数を介して読み取った指定された場所にあるファイルは、XML メタデータ ファイルまたは有効なアセンブリではないように思われます。|  
|WrnUnknownMetadataFound|指定された種類の認識できないメタデータ ドキュメントを保存できません。|  
|ErrDirectoryContainsInvalidCharacters|指定された無効な値が指定されたオプションに渡されました。 指定された文字はパスで使用できません。|  
|WrnCannotResolveServiceForValidation|指定された configName のサービスを読み込めません。 サービスを検証するには、サービス型を含むアセンブリと実行可能ファイルの両方に、該当するサービスの構成を提供してください。|  
|ErrUnexpectedValue|指定されたオプションは値をサポートしていません。|  
|#InvalidArg|指定された対象に無効な引数が含まれています。|  
|ParametersExcludeType|\<type>|  
|HelpXmlSerializer|シリアル化と逆シリアル化に XmlSerializer を使用するデータ型を生成します。|  
|#|---------------------------------------------------------------------------------------------------------------------=|  
|ErrUnexpectedError|ツールでエラーが発生しました。|  
|HelpNologo|著作権とバナー メッセージは表示されません。|  
|ErrInputConflictsWithTarget|指定の値に設定された指定のオプションでは、指定された対象から読み取った入力の種類はサポートされません。|  
|WrnCannotLoadServiceForExport|エクスポートするサービス型の読み込み中にエラーが発生しました。|  
|HelpMetadataDownloadCategory|-= メタデータのダウンロード =-|  
|WrnNoServiceContractTypes|指定されたアセンブリの XmlSerializer 型を生成できません。 サービス コントラクト型が見つかりませんでした。|  
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|指定された対象から読み込んだアセンブリで、型の読み込み中にエラーが発生しました。 アセンブリ内の一部の型は読み込めないため、ツールで使用できません。|  
|ErrDirectoryPointsToAFile|指定された無効な値が指定されたオプションに渡されました。 指定された値はファイルへのパスです。|  
|Error|エラー :|  
|ErrDuplicateReferenceValues|指定されたオプションを使用して、指定されたアセンブリが 2 回読み込まれました。 アセンブリは、1 回しか参照できません。|  
|WrnNoXmlSerializerOperationBehavior|指定されたアセンブリの XmlSerializer を生成できません。 このアセンブリには、XmlSerializerOperationBehavior を使用する操作を含むサービス コントラクトがありません。|  
|ErrCannotCreateDirectory|指定されたディレクトリを作成できません。|  
|ErrCouldNotLoadTypesFromAssemblyAt|指定されたアセンブリ内の型を読み込めません。|  
|ErrUnknownSwitch|指定されたスイッチは認識できないオプションです。|  
|Logo|このツールのロゴは、バージョンが付加された "Microsoft ® Service Model Metadata Tool" です。|  
|NoCodeWasGenerated|コードが生成されませんでした。<br /><br /> クライアントを生成しようとした場合は、この原因として、有効なコントラクトやサービスがメタデータ ドキュメントに含まれていないか、<br /><br /> 検索されたすべてのコントラクト/サービスが参照アセンブリに存在する可能性があります。 すべてのメタデータ ドキュメントをツールに渡したことを確認してください。|  
|WrnUnableToLoadContractForSGen|コントラクトの型の読み込み中にエラーが発生しました。 このコントラクト用の XmlSerializer 型を生成できません。 型と詳細が指定されています。|  
|WrnOptionConflictsWithInput|複数入力アセンブリでは、指定されたオプションを使用できません。 指定されたオプションは無視されます。|  
|ErrUnableToImportMetadata|メタデータをインポートしようとしたときに重大なエラーが発生しました。|  
|ErrInvalidSerializer|シリアライザーの無効な値が指定されたオプションに渡されました。 サポートされているシリアライザーが指定されています。|  
|SavingDownloadedMetadata|ダウンロードしたメタデータ ファイルを保存しています。|  
|WrnNoConfigForServices|渡されたアセンブリが、構成ファイルを含む実行可能ファイルでないか、または、指定された構成名を持つサービスを含む構成ファイルがありません。|  
|ErrInputConflictsWithOption|指定された対象から読み取った入力は、ツール操作の別のモードを意味するため、指定されたオプションと共に使用することはできません。|  
|ErrUnableToExportEndpoints|指定されたサービス型のエクスポート中にエラーが発生しました。|  
|ErrInputSchemaParseError|指定された対象の読み取り中に XML スキーマ解析エラーが発生しました。 XML の形式が正しく、有効であることを確認してください。|  
|ErrInputPolicyParseError|指定された対象の読み取り中に WS-Policy 解析エラーが発生しました。 XML の形式が正しく、有効であることを確認してください。|  
|ErrUnableToLoadReferenceType|参照されたコントラクト型の読み込み中にエラーが発生しました。 この指定された型は無視されます。|  
|WrnCannotLoadServiceForValidation|検証するサービスの読み込み中にエラーが発生しました。 型と詳細が指定されています。|  
|HelpCodeGenerationCategory|-= コードの生成 =-|  
|RetreivingMetadataWithMexAndDisco|WS-Metadata Exchange または DISCO を使用して、指定された対象からメタデータをダウンロードしようとしています。|  
|ErrGeneralSchemaValidation|エクスポート時に生成された XML スキーマの検証中にエラーが発生しました。|  
|ParametersDirectory|\<directory>|  
|ErrCannotLoadSpecifiedType|指定されたオプションに渡された指定された値のための型を読み込めません。 この型が属するアセンブリが、指定されたオプションを使用して指定されていることを確認してください。|  
|ErrOptionModeConflict|指定されたオプションは、別の出力の種類を意味するため、指定されたオプションと共に使用することはできません。|  
|ErrIsNotAnAssembly|指定された対象をアセンブリとして読み込めません。 このファイルが .NET アセンブリであることを確認してください。|  
|ErrInputConflictsWithMode|指定された対象から読み取った入力が、他のオプションと矛盾しています。|  
|ErrDuplicateValuePassedToTypeArg|指定された値が指定されたオプションに繰り返し、渡されました。 各型は 1 回しか指定できません。|  
|ErrInputEPRFileParseError|指定された対象からエンドポイント参照を読み取ることができません。 XML の形式が正しく、有効であることを確認してください。|  
|ErrCouldNotCreateCodeProvider|渡された指定の値に対してコード プロバイダーを作成することはできません、/{1}引数。 コード プロバイダーが適切にインストールおよび構成されていることを確認してください。|  
|ErrPathTooLongDirOnly|結果の指定されたパスが長すぎます。 指定された引数を確認してください。|  
|HelpDataContractSerializer|シリアル化と逆シリアル化に DataContract シリアライザーを使用するデータ型を生成します。|  
|ErrUnableToExportEndpoint|指定された名前空間の指定されたエンドポイント名を、アセンブリに対して読み込んだ構成ファイル内の指定されたサービス型にエクスポートしているときにエラーが発生しました。|  
|HelpUsage1|ヘルプの使用方法を表示します。|  
|HelpUsage2|ヘルプの使用方法を表示します。|  
|HelpUsage3|ヘルプの使用方法を表示します。|  
|HelpUsage4|ヘルプの使用方法を表示します。|  
|HelpUsage5|ヘルプの使用方法を表示します。|  
|ErrDirectoryNotFound|指定されたディレクトリが見つかりません。 このディレクトリが存在することと、このディレクトリを読み取るための適切な権限を持っていることを確認してください。|  
|ErrUnableToLoadFile|指定されたファイルを読み取ることができません。|  
|ErrNoFilesFound|指定された入力パスは、既存のファイルを参照していないように思われます。|  
|ParametersConfig|\<configFile>|  
|ErrDirectoryInsteadOfFile|指定された入力パスは、ディレクトリのように思われます。 URL またはファイル パスを入力する必要があります。|  
|HelpConfig|指定した名前を持つ構成ファイルを生成するようにツールに指示します。 既定 : output.config。|  
|ErrSingleUseSwitch|指定されたオプションを繰り返し指定することはできません。|  
|警告|警告 :|  
|WrnAmbiguousServiceConfig|指定された構成名を持つ複数のサービス構成が見つかりました。次のアセンブリが指定されています。|  
|ErrInvalidInputPath|指定された入力パスは、既存のファイルを参照していないように思われます。また、有効な URI ではないように思われます。|  
|ErrUnableToLoadInputs|読み込まれたメタデータの読み取り中にエラーが発生しました。|  
|GeneratingSerializer|XML シリアライザーを生成しています。|  
|HelpToolConfig|アプリケーション構成ファイルの代わりに使用するカスタム構成ファイル。 これを使用すると、ツールの構成ファイルを変更せずに、メタデータ構成を変更したり、構成の拡張を登録したりできます。|  
|ErrValidateInvalidUse|指定されたオプションを指定されたオプションと共に使用することはできません。|  
|WrnWSMExFailed|指定された URI で WS-Metadata Exchange Error が発生しました。|  
|HelpNoconfig|構成を生成しません。|  
|HelpCodeGenerationDescription|指定された対象は、サービス コントラクト、クライアント、およびデータ型をメタデータ ドキュメントから生成できます。|  
|HelpTargetMetadata|メタデータを出力します。 入力が URL の場合、Svcutil.exe はメタデータをディスクに保存し、コードを生成しません。 入力が 1 つ以上のアセンブリの場合、Svcutil.exe は、アセンブリ内の型からメタデータを生成します。|  
|ErrAmbiguousOptionModeConflict|指定されたオプションは、他のオプションと競合しています。 ツールの使用法を確認してください。|  
|ErrNotLanguageOrCodeDomType|指定された引数に渡された指定された値は、定義された言語を表していないため、完全修飾された CLR 型として読み込めません。|  
|ErrUnableToUniquifyFilename|出力ファイル名を作成できません。 指定されたプレフィックスを使用して作成されているファイルが多すぎます。|  
|ErrCannotCreateFile|指定された出力ファイルを作成できません。|  
|ErrExpectedValue|指定されたオプションには値を指定する必要があります。|  
|ErrCannotDisambiguateSpecifiedTypes|同じ名前を持つ複数の型が参照アセンブリのセットに存在します。 指定されたオプションで、アセンブリ修飾名を使用して指定された型を区別してください。|  
|RetreivingMetadataWithMexOnly|WS-Metadata Exchange を使用して、指定された場所からメタデータをダウンロードしようとしています。 この URL は DISCO をサポートしていません。|  
|ErrInvalidTarget|指定されたターゲットは、指定されたオプションを使用して指定した場合は無効です。 サポートされているターゲットが指定されています。|  
|ErrPathTooLong|結果のパスが長すぎます。 指定された引数をレビューしてください。|  
|HelpCommonOptionsCategory|-= 共通のオプション =-|  
|ParametersServiceName|\<serviceConfigName>|  
|ErrNoValidInputFilesSpecified|有効な入力ファイルが指定されていません。 メタデータ ドキュメントまたはアセンブリ ファイルを指定してください。|  
|ParametersLanguage|\<language>|  
|ErrUnableToLoadMetadataDocument|読み込んだドキュメントの 1 つからメタデータを読み取っているときにエラーが発生しました。 ドキュメント識別子が指定されています。|  
|ErrConflictingInputs|指定された入力引数は、ツール操作の別のモードを意味するため、指定された対象と競合しています。|  
|WrnUnableToLoadContractForValidation|コントラクトの型の読み込み中にエラーが発生しました。 型と詳細が指定されています。|  
|WrnAttributeReflectionErrors|指定された対象から読み込んだアセンブリ内の一部の型で、属性のリフレクションに失敗しました。 このアセンブリが、適切なセキュリティ特権を使用してこの場所から読み込むことができることを確認してください。|  
|HelpMetadataExportCategory|-= メタデータのエクスポート =-|  
|HelpValidationCategory|-= サービスの検証 =-|  
|ValidationError|検証エラー :|  
|GeneratingFiles|ファイルを生成しています...|  
|ErrCannotSpecifyMultipleMappingsForNamespace|無効な値が、指定されたオプションに渡されました。 指定されたターゲット名前空間は、指定された複数の CLR 名前空間にマップできません。|  
|ErrCouldNotLoadReferenceAssemblyAt|指定された参照アセンブリを読み込めません。|  
|ParametersOut|\<file>|  
|NoCodeWasGeneratedSuggestDCOnly|スキーマからコントラクトを生成するには、指定されたオプションを使用してください。|  
|ErrUnableToLoadInputConfig|指定された構成ファイルを読み込むことができません。|  
|ErrUnexpectedDelimiter|オプションの先頭には、無効な引数区切り記号 (':' または '=') を使用できません。|  
|ErrMergeConfigUsedWithoutConfig|もう一方の指定されたオプションを指定せずに、指定されたオプションを使用することはできません。|  
|ErrUnableToExportContract|指定された型から読み込んだコントラクトのエクスポート中にエラーが発生しました。|  
|GeneratingMetadata|メタデータ ファイルを生成しています。|  
|ErrNotCodeDomType|指定された引数に渡された指定された型は、指定された派生クラスの型ではありません。|  
|WrnNoTypeForServices|渡されたアセンブリには、指定された構成名を持つサービス型を含むものがありません。|  
|ErrAssemblyLoadFailed|指定されたファイルをアセンブリとして読み込めません。 詳細については、「FusionLogs」を参照してください。|  
|NoMetadataWasGenerated|メタデータ ファイルが生成されませんでした。 エクスポートされたサービス コントラクトはありません。<br /><br /> サービスをエクスポートするには、指定されたオプションを使用してください。 データ コントラクトをエクスポートするには、オプションを指定してください。|  
|WrnCannotResolveServiceForExport|指定された configName のサービスを読み込めません。 サービスをエクスポートするには、サービス型を含むアセンブリと実行可能ファイルに、該当するサービスの構成を提供してください。|  
|ParametersCollectionType|\<type>|  
|ErrOptionConflictsWithTarget|指定の値に設定された指定のオプションでは、指定されたオプションの使用がサポートされません。|  
|ErrCodegenError|指定された言語でコードを生成しているときにエラーが発生しました。<br /><br /> この言語は、生成されているすべてのコード要素をサポートしているわけではありません。 別の言語を使用してください。|  
|ErrInputWsdlParseError|指定された対象の読み取り中に WSDL 解析エラーが発生しました。 XML の形式が正しく、有効であることを確認してください。|  
|ErrCouldNotCreateInstance|指定された引数に渡された指定された型のインスタンスを作成できません。|  
|ParametersNamespace|\<string,string>|  
|HelpNostdlib|標準ライブラリを参照しません (既定では、mscorlib.dll と system.servicemodel.dll が参照されます)。|  
|WrnCannotLoadConfigFileForExport|指定された対象から読み込んだ構成ファイルの処理中にエラーが発生しました。 この構成ファイルで定義されているサービスを読み込むことができません。|  
|WrnUnableToLoadContractForExport|コントラクトの型の読み込み中にエラーが発生しました。 この指定された型はエクスポートできません。|
