---
title: データ コントラクト サロゲート
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: f97826cb5154035b535b5eac3a8818d8b366d639
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858027"
---
# <a name="data-contract-surrogates"></a>データ コントラクト サロゲート
データ コントラクト*サロゲート*は高度な機能、データ コントラクト モデルに基づいて構築されています。 この機能は、型をシリアル化または逆シリアル化する方法や、型をメタデータに投影する方法をユーザーが変更する場合に、型のカスタマイズと置換に使用することを目的としています。 サロゲートを使用できるのは、型のデータ コントラクトが指定されていない場合、フィールドやプロパティが <xref:System.Runtime.Serialization.DataMemberAttribute> 属性でマークされていない場合、またはユーザーがスキーマのバリエーションを動的に作成することを希望している場合などです。  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> を使用して .NET Framework から XML などの適切な形式に変換するときに、データ コントラクト サロゲートを使用してシリアル化と逆シリアル化を行います。 また、XML スキーマ ドキュメント (XSD) などのメタデータ表現を生成するときに、データ コントラクト サロゲートを使用して、型のエクスポートするメタデータを変更できます。 インポート時には、メタデータからコードが作成されますが、この場合にサロゲートを使用すると、生成されるコードもカスタマイズできます。  
  
## <a name="how-the-surrogate-works"></a>サロゲートのしくみ  
 サロゲートは、ある型 ("元の" 型) を別の型 ("サロゲートされた" 型) に割り当てることによって機能します。 元の型 `Inventory` と新しいサロゲート型 `InventorySurrogated` の例を以下に示します。 `Inventory` 型はシリアル化できませんが、`InventorySurrogated` 型は以下のようになります。  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 このクラスにはデータ コントラクトが定義されていないため、このクラスをデータ コントラクトを持つサロゲート クラスに変換します。 サロゲートされたクラスの例を次に示します。  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>IDataContractSurrogate の実装  
 データ コントラクト サロゲートを使用するには、<xref:System.Runtime.Serialization.IDataContractSurrogate> インターフェイスを実装します。  
  
 考えられる実装での <xref:System.Runtime.Serialization.IDataContractSurrogate> の各メソッドの概要を以下に示します。  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> メソッドは、ある型を別の型に割り当てます。 これは、シリアル化、逆シリアル化、インポート、およびエクスポートに必須のメソッドです。  
  
 最初のタスクとして、他の型に割り当てる型を定義します。 例:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   シリアル化では、後で <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> メソッドを呼び出して、元のインスタンスをサロゲートされたインスタンスに変換する際に、このメソッドによって返されたマッピングが使用されます。  
  
-   逆シリアル化では、サロゲート型のインスタンスに逆シリアル化する際に、シリアライザーはこのメソッドによって返されたマッピングを使用します。 その後、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> が呼び出されて、サロゲートされたインスタンスが元の型のインスタンスに変換されます。  
  
-   エクスポートでは、メタデータの生成に使用するデータ コントラクトを取得する際に、このメソッドによって返されたサロゲート型が反映されます。  
  
-   インポートでは、最初の型がサロゲート型に変更されます。このサロゲート型は、参照のサポートなどの目的で使用するデータ コントラクトを取得する際に反映されます。  
  
 <xref:System.Type> パラメーターは、シリアル化、逆シリアル化、インポート、またはエクスポートするオブジェクトの型です。 サロゲートが型を処理しない場合、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> メソッドは入力の型を返す必要があります。 それ以外の場合は、サロゲートされた適切な型を返します。 複数のサロゲート型が存在する場合は、このメソッドで多数のマッピングを定義できます。  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> メソッドは、組み込みのデータ コントラクト プリミティブ (<xref:System.Int32> や <xref:System.String> など) に対しては呼び出されません。 その他の型 (配列、ユーザー定義型、その他のデータ構造体など) については、このメソッドは各型に対して呼び出されます。  
  
 前の例では、このメソッドは `type` パラメーターと `Inventory` が比較可能かどうかをチェックします。 比較可能な場合は、`InventorySurrogated` に割り当てます。 シリアル化、逆シリアル化、インポート スキーマ、またはエクスポート スキーマを呼び出すときは、常にこの関数が最初に呼び出されて、型間のマッピングが確認されます。  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize Method  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> メソッドは、元の型のインスタンスをサロゲートされた型のインスタンスに変換します。 これは、シリアル化に必須のメソッドです。  
  
 次の手順では、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> メソッドを実装して、物理データを元のインスタンスからサロゲートに割り当てる方法を定義します。 例:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> メソッドは、オブジェクトをシリアル化するときに呼び出されます。 このメソッドでは、元の型からサロゲートされた型のフィールドにデータを転送します。 フィールドは、サロゲート フィールドに直接割り当てることができます。また、元のデータの操作をサロゲートに格納することもできます。 このメソッドは、フィールドを直接割り当てる場合、サロゲートされたフィールドに格納されたデータに対して操作を実行する場合、サロゲートされたフィールドに元の型の XML を格納する場合などに使用できます。  
  
 `targetType` パラメーターは、メンバーの宣言された型を指します。 このパラメーターは、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> メソッドによって返されたサロゲートされた型です。 シリアライザーは、返されるオブジェクトがこの型に割り当て可能であることを強制するわけではありません。 `obj`パラメーターは、シリアル化するオブジェクトに応じてサロゲートに変換されます。 サロゲートがオブジェクトを処理しない場合、このメソッドは入力オブジェクトを返す必要があります。 それ以外の場合は、新しいサロゲート オブジェクトが返されます。 オブジェクトが null の場合、サロゲートは呼び出されません。 さまざまなインスタンスの多数のサロゲートのマッピングをこのメソッドで定義できます。  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> の作成時に、オブジェクト参照を保持するように指定できます  (詳細については、次を参照してください[シリアル化および逆シリアル化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。)。これを行うには、コンストラクターの `preserveObjectReferences` パラメーターを `true` に設定します。 この場合、サロゲートはオブジェクトに対して 1 回だけ呼び出されます。これは、以降のシリアル化では参照をストリームに書き込むだけだからです。 `preserveObjectReferences` を `false` に設定すると、インスタンスが発生するたびにサロゲートが呼び出されます。  
  
 シリアル化されたインスタンスの型が宣言された型と異なる場合、インスタンスをもう一方の側で逆シリアル化できるように、型情報 (`xsi:type` など) がストリームに書き込まれます。 このプロセスは、オブジェクトがサロゲートされているかどうかに関係なく発生します。  
  
 前述の例では、`Inventory` インスタンスのデータが `InventorySurrogated` のデータに変換されます。 オブジェクトの型がチェックされ、サロゲートされた型に変換するために必要な処理が実行されます。 この場合、`Inventory` クラスの各フィールドは、`InventorySurrogated` クラスのフィールドに直接コピーされます。  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject Method  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> メソッドは、サロゲートされた型のインスタンスを元の型のインスタンスに変換します。 これは、逆シリアル化に必須のメソッドです。  
  
 次のタスクとして、サロゲート インスタンスから元のインスタンスに物理データを割り当てる方法を定義します。 例:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 このメソッドが呼び出されるのは、オブジェクトの逆シリアル化中だけです。 このメソッドは、サロゲート型から元の型に戻す逆シリアル化に必要な逆方向のデータ マッピングを行います。 `GetObjectToSerialize` メソッドと同様に、フィールド データを直接交換する場合、データに対して操作を実行する場合、XML データを格納する場合などに使用できます。 逆シリアル化するときには、データ変換時の操作の結果として、元のデータから正確なデータ値を必ずしも取得できるとは限りません。  
  
 `targetType` パラメーターは、メンバーの宣言された型を指します。 このパラメーターは、`GetDataContractType` メソッドによって返されたサロゲートされた型です。 `obj`パラメーターは逆シリアル化されたオブジェクトを指します。 オブジェクトがサロゲートされている場合、オブジェクトを変換して元の型に戻すことができます。 サロゲートがオブジェクトを処理しない場合、このメソッドは入力オブジェクトを返します。 それ以外の場合は、変換が完了すると、逆シリアル化されたオブジェクトが返されます。 複数のサロゲート型が存在する場合、各型とその変換を示すことにより、サロゲートからそれぞれのプライマリ型へのデータ変換を提供できます。  
  
 オブジェクトを返す場合、このサロゲートによって返されたオブジェクトで内部オブジェクト テーブルが更新されます。 インスタンスへの以降の参照では、このオブジェクト テーブルからサロゲートされたインスタンスが取得されます。  
  
 前の例では、`InventorySurrogated` 型のオブジェクトが最初の `Inventory` 型に変換されます。 この場合、データは `InventorySurrogated` から `Inventory` の対応するフィールドに直接転送されます。 データ操作は発生しないため、各メンバー フィールドにはシリアル化前と同じ値が格納されます。  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport Method  
 スキーマをエクスポートする場合、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> メソッドは省略可能です。 このメソッドは、エクスポートするスキーマに追加データやヒントを挿入するために使用します。 追加データは、メンバー レベルまたは型レベルで挿入できます。 例:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 このメソッド (2 つのオーバーロードを持ちます) を使用すると、メンバー レベルまたは型レベルで、追加情報をメタデータに含めることができます。 メンバーが public と private のどちらであるかに関するヒントや、スキーマのエクスポートとインポート全体を通じて保持されるコメントを含めることができます。 このメソッドを使用しない場合、このような情報は失われます。 このメソッドは、メンバーまたは型の挿入や削除を行うのではなく、メンバー レベルまたは型レベルでスキーマに付加的なデータを追加します。  
  
 このメソッドのオーバーロードでは、`Type` (`clrtype` パラメーター) または <xref:System.Reflection.MemberInfo> (`memberInfo` パラメーター) を取得できます。 2 番目のパラメーターは、常に `Type` (`dataContractType` パラメーター) です。 このメソッドは、サロゲートされた `dataContractType` 型のすべてのメンバーと型に対して呼び出されます。  
  
 どちらのオーバーロードでも、`null` またはシリアル化可能なオブジェクトを返す必要があります。 null 以外のオブジェクトは、エクスポートするスキーマに注釈としてシリアル化されます。 `Type` オーバーロードでは、スキーマにエクスポートされる各型は、`dataContractType` パラメーターのサロゲートされた型と共に、最初のパラメーターでこのメソッドに送信されます。 `MemberInfo` オーバーロードでは、スキーマにエクスポートされる各メンバーが、2 番目のパラメーターのサロゲートされた型と共に `memberInfo` パラメーターとして情報を送信します。  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>GetCustomDataToExport Method (Type, Type)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> メソッドは、すべての型定義のスキーマのエクスポート中に呼び出されます。 このメソッドは、エクスポート時にスキーマ内の型に情報を追加します。 スキーマに含める必要のある追加データがあるかどうかを確認するために、定義済みの各型がこのメソッドに送信されます。  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport Method (MemberInfo, Type)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> は、エクスポートする型のすべてのメンバーのエクスポート中に呼び出されます。 この関数を使用すると、エクスポート時にスキーマに含めるメンバーに関するコメントをカスタマイズできます。 スキーマに付加的なデータを追加する必要があるかどうかをチェックするために、クラスの各メンバーの情報がこのメソッドに送信されます。  
  
 前述の例では、サロゲートの各メンバーの `dataContractType` が検索されます。 検索後、各フィールドの適切なアクセス修飾子が返されます。 このカスタマイズを行わない場合、アクセス修飾子の既定値は public です。 したがって、実際のアクセス制限には関係なく、エクスポートされたスキーマを使用して生成されるコードでは、すべてのメンバーが public として定義されます。 この実装を使用しない場合、`numpens` メンバーは、サロゲートで private として定義されている場合でも、エクスポートされたスキーマでは public になります。 このメソッドを使用することにより、エクスポートされるスキーマで、アクセス修飾子を private として生成できます。  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport Method  
 このメソッドは、サロゲートの <xref:System.Type> を元の型に割り当てます。 スキーマのインポートでは、このメソッドは省略可能です。  
  
 スキーマをインポートし、そのコードを生成するサロゲートを作成したら、次の作業として、元の型に対してサロゲート インスタンスの型を定義します。  
  
 生成されるコードで既存のユーザー型を参照する必要がある場合は、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> メソッドを実装してこれを行います。  
  
 スキーマをインポートするときに、サロゲートされたデータ コントラクトを型に割り当てるために、すべての型宣言に対してこのメソッドが呼び出されます。 `typeName` および `typeNamespace` の各文字列パラメーターでは、サロゲートされた型の名前と名前空間が定義されます。 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> の戻り値は、新しい型を生成する必要があるかどうかを判断するために使用されます。 このメソッドは、有効な型または null のいずれかを返す必要があります。 有効な型を返す場合、返される型は生成されるコード内で参照される型として使用されます。 null を返す場合は、型が参照されることはないため、新しい型を作成する必要があります。 複数のサロゲートが存在する場合は、各サロゲート型から最初の型へのマッピングを実行できます。  
  
 `customData` パラメーターは、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> から最初に返されたオブジェクトです。 この `customData` は、サロゲート作成者が、コードを生成するためにインポート時に使用するメタデータに追加情報やヒントを挿入する場合に使用します。  
  
### <a name="processimportedtype-method"></a>ProcessImportedType メソッド  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> メソッドは、スキーマのインポートから作成された型をカスタマイズします。 このメソッドは省略可能です。  
  
 スキーマをインポートするときに、このメソッドを使用すると、インポートする型とコンパイルの情報をカスタマイズできます。 例:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 インポート中に、このメソッドは生成されるすべての型に対して呼び出されます。 指定した <xref:System.CodeDom.CodeTypeDeclaration> を変更するか、<xref:System.CodeDom.CodeCompileUnit> を変更します。 これには、`CodeTypeDeclaration` の名前、メンバー、属性、および他のさまざまなプロパティの変更が含まれます。 `CodeCompileUnit` を処理することにより、ディレクティブ、名前空間、参照アセンブリ、および他のいくつかの側面を変更できます。  
  
 `CodeTypeDeclaration` パラメーターには、DOM コードの型宣言が含まれます。 `CodeCompileUnit` パラメーターでは、コードの処理に関する変更を行うことができます。  `null` を返すと、型宣言が破棄されます。 `CodeTypeDeclaration` を返すと、変更が保持されます。  
  
 メタデータのエクスポート時にカスタム データを挿入した場合は、インポート時にこのデータをユーザーに提供して、データを使用できるようにする必要があります。 このカスタム データは、プログラミング モデルのヒントやその他のコメントに使用できます。 各 `CodeTypeDeclaration` と <xref:System.CodeDom.CodeTypeMember> インスタンスには、<xref:System.CodeDom.CodeObject.UserData%2A> 型にキャストされる `IDataContractSurrogate` プロパティとしてカスタム データが含まれます。  
  
 前述の例では、インポートするスキーマに対して変更が行われています。 コードでは、サロゲートを使用して元の型の private メンバーを保持しています。 スキーマをインポートするときの既定のアクセス修飾子は `public` です。 したがって、この例のように変更しない限り、サロゲート スキーマのすべてのメンバーは public になります。 エクスポート中に、どのメンバーが private であるかに関するカスタム データがメタデータに挿入されます。 この例では、カスタム データを調べ、アクセス修飾子が private かどうかをチェックした後、属性を設定することで適切なメンバーを private に変更しています。 このカスタマイズを行わない場合、`numpens` メンバーは、private ではなく public として定義されます。  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes メソッド  
 このメソッドは、スキーマから定義済みのカスタム データ型を取得します。 スキーマのインポートでは、このメソッドは省略可能です。  
  
 このメソッドは、スキーマのエクスポートとインポートの開始時に呼び出されます。 このメソッドは、エクスポートまたはインポートするスキーマで使用されるカスタム データ型を返します。 メソッドには、型のコレクションである <xref:System.Collections.ObjectModel.Collection%601> (`customDataTypes` パラメーター) が渡されます。 このメソッドでは、既知の型をこのコレクションに追加する必要があります。 既知のカスタム データ型は、<xref:System.Runtime.Serialization.DataContractSerializer> を使用したカスタム データのシリアル化と逆シリアル化を可能にするために必要となります。 詳細については、次を参照してください。 [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)します。  
  
## <a name="implementing-a-surrogate"></a>サロゲートの実装  
 Wcf データ コントラクト サロゲートを使用するには、いくつかの特別な手順に従ってください。  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>シリアル化と逆シリアル化にサロゲートを使用するには  
 サロゲートを使用してデータのシリアル化と逆シリアル化を実行するには、<xref:System.Runtime.Serialization.DataContractSerializer> を使用します。 <xref:System.Runtime.Serialization.DataContractSerializer> は、<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> によって作成されます。 サロゲートも指定する必要があります。  
  
##### <a name="to-implement-serialization-and-deserialization"></a>シリアル化と逆シリアル化を実装するには  
  
1. サービスの <xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。 完全な手順については、次を参照してください。[基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)します。  
  
2. 指定したサービス ホストの各 <xref:System.ServiceModel.Description.ServiceEndpoint> について、<xref:System.ServiceModel.Description.OperationDescription> を検索します。  
  
3. 操作の動作を検索して、<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> のインスタンスが見つかるかどうかを確認します。  
  
4. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> が見つかった場合、<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> プロパティをサロゲートの新しいインスタンスに設定します。 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> が見つからなかった場合は、新しいインスタンスを作成し、新しい動作の <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> メンバーをサロゲートの新しいインスタンスに設定します。  
  
5. 最後に、次の例に示すように、この新しい動作を現在の操作の動作に追加します。  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>メタデータのインポートにサロゲートを使用するには  
 WSDL や XSD などのメタデータをインポートしてクライアント側のコードを生成する場合、XSD スキーマからコードを生成するコンポーネント (<xref:System.Runtime.Serialization.XsdDataContractImporter>) にサロゲートを追加する必要があります。 これを行うには、メタデータをインポートする際に使用する <xref:System.ServiceModel.Description.WsdlImporter> を直接変更します。  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>メタデータのインポートに使用するサロゲートを実装するには  
  
1. <xref:System.ServiceModel.Description.WsdlImporter> クラスを使用して、メタデータをインポートします。  
  
2. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> メソッドを使用して、<xref:System.Runtime.Serialization.XsdDataContractImporter> が定義されているかどうかをチェックします。  
  
3. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> メソッドが `false` を返した場合、新しい <xref:System.Runtime.Serialization.XsdDataContractImporter> を作成し、<xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> プロパティを <xref:System.Runtime.Serialization.ImportOptions> クラスの新しいインスタンスに設定します。 それ以外の場合は、`out` メソッドの <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> パラメーターによって返されたインポーターを使用します。  
  
4. <xref:System.Runtime.Serialization.XsdDataContractImporter> に <xref:System.Runtime.Serialization.ImportOptions> が定義されていない場合は、このプロパティを <xref:System.Runtime.Serialization.ImportOptions> クラスの新しいインスタンスとして設定します。  
  
5. <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> の <xref:System.Runtime.Serialization.ImportOptions> の <xref:System.Runtime.Serialization.XsdDataContractImporter> プロパティを、サロゲートの新しいインスタンスに設定します。  
  
6. <xref:System.Runtime.Serialization.XsdDataContractImporter> クラスから継承した <xref:System.ServiceModel.Description.MetadataExporter.State%2A> の <xref:System.ServiceModel.Description.WsdlImporter> プロパティによって返されたコレクションに、<xref:System.ServiceModel.Description.MetadataExporter> を追加します。  
  
7. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> の <xref:System.ServiceModel.Description.WsdlImporter> メソッドを使用して、スキーマ内のすべてのデータ コントラクトをインポートします。 この最後の手順で、サロゲートを呼び出すことによって読み込まれたスキーマからコードが生成されます。  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>メタデータのエクスポートにサロゲートを使用するには  
 既定では、wcf サービスのメタデータをエクスポートするときに、WSDL と XSD スキーマを生成する必要があります。 データ コントラクト型の XSD スキーマを生成するコンポーネント (<xref:System.Runtime.Serialization.XsdDataContractExporter>) に、サロゲートを追加する必要があります。 これを行うには、<xref:System.ServiceModel.Description.IWsdlExportExtension> を実装する動作を使用して <xref:System.ServiceModel.Description.WsdlExporter> を変更するか、メタデータをエクスポートする際に使用する <xref:System.ServiceModel.Description.WsdlExporter> を直接変更します。  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>メタデータのエクスポートにサロゲートを使用するには  
  
1. 新しい <xref:System.ServiceModel.Description.WsdlExporter> を作成するか、`wsdlExporter` メソッドに渡された <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> パラメーターを使用します。  
  
2. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 関数を使用して、<xref:System.Runtime.Serialization.XsdDataContractExporter> が定義されているかどうかをチェックします。  
  
3. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> が `false` を返した場合、<xref:System.Runtime.Serialization.XsdDataContractExporter> から生成された XML スキーマを使用して新しい <xref:System.ServiceModel.Description.WsdlExporter> を作成し、<xref:System.ServiceModel.Description.MetadataExporter.State%2A> の <xref:System.ServiceModel.Description.WsdlExporter> プロパティによって返されたコレクションに追加します。 それ以外の場合は、`out` メソッドの <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> パラメーターによって返されたエクスポーターを使用します。  
  
4. <xref:System.Runtime.Serialization.XsdDataContractExporter> に <xref:System.Runtime.Serialization.ExportOptions> が定義されていない場合は、<xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> プロパティを <xref:System.Runtime.Serialization.ExportOptions> クラスの新しいインスタンスに設定します。  
  
5. <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> の <xref:System.Runtime.Serialization.ExportOptions> の <xref:System.Runtime.Serialization.XsdDataContractExporter> プロパティを、サロゲートの新しいインスタンスに設定します。 メタデータをエクスポートするための以降の手順を変更する必要はありません。  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
