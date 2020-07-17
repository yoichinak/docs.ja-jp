---
title: サービス フレームワークのメタデータ
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f3e73df54b3389b2c9f27001953be147b27eb6f8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991212"
---
# <a name="service-framework-metadata"></a>サービス フレームワークのメタデータ
ここでは、サービス フレームワーク メタデータによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|非同期 End が間違ったチャネルで呼び出されました。|  
|AsyncEndCalledWithAnIAsyncResult|非同期 End が別の Begin メソッドから IAsyncResult を指定して呼び出されました。|  
|AttemptedToGetContractTypeForButThatTypeIs1|指定されたのコントラクト型を取得しようとしました。 種類が ServiceContract ではなく、ServiceContract を継承していません。|  
|CannotHaveTwoOperationsWithTheSameName3|同じ名前の 2 つの操作を同一のコントラクトに含めることはできません。 指定された型の指定されたメソッドは、このルールに違反しています。 いずれかの操作の名前を変更するには、メソッド名を変更するか、OperationContractAttribute の Name プロパティを使用します。|  
|CannotInheritTwoOperationsWithTheSameName3|同じ名前を持つ 2 つの異なる操作を継承することはできません。 指定されたコントラクトの指定された操作は、このルールに違反しています。 いずれかの操作の名前を変更するには、メソッド名を変更するか、OperationContractAttribute の Name プロパティを使用します。|  
|CantCreateChannelWithManualAddressing|要求/応答が必要なコントラクト、および双方向の通信のみをサポートする手動によるアドレス指定が必要なバインドのチャネルを作成することができません。|  
|DuplicateBehavior1|値をコレクションに追加できません。 コレクションには、指定された同じ型の項目が既に含まれています。 このコレクションは、各型のインスタンスを 1 つだけサポートします。|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|指定された基本サービス コントラクトは指定されたコールバック コントラクトを持つため、指定された派生サービス コントラクトも、指定された型または派生型をコールバック コントラクトとして指定する必要があります。|  
|InvalidAsyncBeginMethodSignatureForMethod2|指定された ServiceContract 型の指定されたメソッドの非同期 Begin メソッドの署名が無効です。 Begin メソッドは、AsyncCallback およびオブジェクトを最後の 2 つの引数として受け取って、IAsyncResult を返す必要があります。|  
|InvalidAsyncEndMethodSignatureForMethod2|指定された ServiceContract 型の指定されたメソッドの非同期 End メソッドの署名が無効です。 End メソッドは、IAsyncResult を最後の引数として受け取る必要があります。|  
|MessagePropertiesArraySize0|渡された配列には、このコレクションに含まれるすべてのプロパティを保持するだけの容量がありません。|  
|OneWayAndFaultsIncompatible2|指定された型の指定されたメソッドでは、IsOneWay=true が設定されており、1 つ以上の FaultContractAttributes が宣言されています。 一方向のメソッドでは FaultContractAttributes を宣言できません。 IsOneWay を false に変更するか、FaultContractAttribute を削除してください。|  
|UnsupportedWSDLOnlyOneMessage|サポートされていない Web サービス記述言語。 エラー メッセージには、1 つのメッセージ部のみがサポートされています。 このエラー メッセージは、複数のメッセージ部を参照しています。 WSDL ファイルへの編集アクセス権がある場合は、余分なメッセージ部を削除してエラー メッセージが 1 つのメッセージ部のみを参照するようにすることで問題を修正できます。|  
|UnsupportedWSDLTheFault|サポートされていない Web サービス記述言語。 エラー メッセージ部は 1 つの要素だけを参照する必要があります。 このエラー メッセージは要素を参照していません。 この WSDL ドキュメントへの編集アクセス権がある場合は、'element' 属性を使用してスキーマ要素を参照することでこの問題を修正できます。|  
|WsdlImportErrorDependencyDetail|指定された他の値が依存する指定された対象のインポート中にエラーが発生しました。 Xpath も指定されています。|  
|XsdMissingRequiredAttribute1|指定された必須の属性がありません。|
