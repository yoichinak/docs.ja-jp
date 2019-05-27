---
title: MissingRuntimeArtifactException クラス (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 246584a34d6a3a8aaf4cac9845e8bb77d1654fa1
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052432"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException クラス (.NET ネイティブ)
**Windows 10、.NET ネイティブのみの Windows アプリ用 .NET**  
  
 この例外は、型または型のメンバーのメタデータは使用可能だが、その実装が削除されている場合にスローされます。  
  
 **名前空間:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingRuntimeArtifactException`クラスが、.NET ネイティブ ツール チェーンによって内部使用のみを対象としています。 サード パーティのコードで使用することを目的としていません。また、アプリケーション コードで、例外を処理する必要はありません。 代わりに、[ランタイム ディレクティブ ファイル](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)にエントリを追加することにより、例外を除去します。 詳細については、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 `MissingRuntimeArtifactException` クラスが <xref:System.MemberAccessException> から派生していることに注意してください。  
  
 `MissingRuntimeArtifactException` クラスには次のメンバーがあります。  
  
## <a name="constructors"></a>コンストラクター  
  
|コンストラクター|説明|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|エラーを説明するシステム提供のメッセージを使用して、`MissingRuntimeArtifactException` クラスの新しいインスタンスを初期化します。<br /><br /> このコンス トラクターは、.NET ネイティブ ツール チェーンでのみによって内部的に使用します。|  
|`public MissingRuntimeArtifactException(String message)`|指定したエラー メッセージを使用して、`MissingRuntimeArtifactException` クラスの新しいインスタンスを初期化します。<br /><br /> このコンス トラクターは、.NET ネイティブ ツール チェーンでのみによって内部的に使用します。|  
  
## <a name="properties"></a>プロパティ  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|例外に関する追加のユーザー定義情報を提供する、キー/値ペアのコレクションを取得します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public string HelpLink { get; set; }`|この例外に関連付けられているヘルプ ファイルへのリンクを取得または設定します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public int HResult { get; protected set; }`|特定の例外に割り当てられた、コード化された数値である、`HRESULT` を取得または設定します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public Exception InnerException { get; }`|現在の例外を引き起こした例外を取得します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public string Message { get; }`|現在の例外を説明するメッセージを取得します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public string Source { get; set; }`|エラーの原因になったアプリケーションまたはオブジェクトの名前を取得または設定します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public string StackTrace { get; }`|呼び出し履歴で直前のフレームの文字列形式を取得します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public MethodBase TargetSite { get; }`|現在の例外をスローしたメソッドを取得します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。  (<xref:System.Object> から継承。)|  
|`protected void Finalize()`|オブジェクトが、ガベージ コレクションによって収集される前に、リソースの解放とその他のクリーンアップ操作の実行を試みることができるようにします。 (<xref:System.Object> から継承。)|  
|`public Exception GetBaseException()`|1 つ以上の後続の例外の根本原因である例外を返します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public int GetHashCode()`|`MissingRuntimeArtifactException` インスタンスのハッシュ コードを返します。   (<xref:System.Object> から継承。)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|例外に関する情報を使用して、<xref:System.Runtime.Serialization.SerializationInfo> オブジェクトを設定します。  (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`public Type GetType()`|現在のインスタンスのランタイム型を取得します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
|`protected Object MemberwiseClone()`|現在のオブジェクトの簡易コピーを作成します。 (<xref:System.Object> から継承。)|  
|`public string ToString()`|現在の例外の文字列形式を返します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
  
## <a name="events"></a>イベント  
  
|event|説明|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|例外がシリアル化され、例外に関するシリアル化されたデータを含む例外状態オブジェクトが作成されたときに発生します。 (<xref:System.Exception?displayProperty=nameWithType> から継承。)|  
  
## <a name="usage-details"></a>使用方法の詳細  
 `MissingRuntimeArtifactException` 例外は、型のインスタンス化または型のメンバーの呼び出しが試行され、その型またはメンバーのメタデータは存在するが、実装が削除されている場合にスローされます。  
  
 ランタイム ディレクティブ (XML 構成) ファイルで、によって定義されるかどうかメタデータと、実装コード メソッドを動的に実行するのには、アプリに対して使用できる実行時に\*。 (rd.xml)。 アプリからこの例外がスローされないようにするには、\*.rd.xml を変更して、型または型のメンバーが必要とするメタデータが実行時に確実に存在するようにする必要があります。 \*.rd.xml ファイルの形式の詳細については、「[Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」(ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス) を参照してください。  
  
> [!IMPORTANT]
>  この例外はアプリケーションで必要な実装コードを実行時に使用できないことを示しているため、この例外を `try`/`catch` ブロックで処理しないでください。 代わりに、ランタイム ディレクティブ ファイルを使用して、例外の原因を診断して排除する必要があります。 通常、適切なを指定することによってこの例外を排除`Activate`または`Dynamic`、ランタイム ディレクティブ ファイル内のプログラム要素のポリシー (\*.rd.xml ファイル)。 例外を除去するためにランタイム ディレクティブ ファイルに追加できるエントリを取得するには、次の 2 つのトラブルシューティング ツールのいずれかを使用できます。  
>   
> - [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。  
> - [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。  
  
 `MissingRuntimeArtifactException` クラスには一意のメンバーは含まれていません。メンバーはすべて基底クラスの <xref:System.MemberAccessException> から継承されます。  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
