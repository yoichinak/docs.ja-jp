---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929982"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter.CreateConverter 署名が変更されました

<xref:System.Text.Json.Serialization.JsonConverterFactory> クラスの合成を容易にするために、<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> メソッドが公開され、<xref:System.Text.Json.JsonSerializerOptions> 型の 2 番目の引数が指定されました。

#### <a name="details"></a>説明

.NET Core バージョン 3.0 Preview 8 より前の `CreateConverter` メソッドの署名は次のとおりです。 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

.NET Core 3.0 Preview 8 以降のバージョンでは、次のようになります。

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

この変更の前は、シールド ファクトリ コンバーターを作成することは、そこから <xref:System.Text.Json.Serialization.JsonConverter%601> を取得する簡単な方法がなかったため困難でした。 ファクトリ メソッドを公開し、現在の <xref:System.Text.Json.JsonSerializerOptions> も渡すことによって、より柔軟な作成を行うことができます。

#### <a name="version-introduced"></a>導入されたバージョン

3.0 Preview 8

#### <a name="recommended-action"></a>推奨される操作

派生クラスを更新して再コンパイルする必要があります。

#### <a name="affected-apis"></a>影響を受ける API

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>。

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
