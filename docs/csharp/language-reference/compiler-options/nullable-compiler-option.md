---
title: -nullable (C# コンパイラ オプション)
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: a68255dba18a022784cd4aaf0027c371893c577b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "84449799"
---
# <a name="-nullable-c-compiler-options"></a>-nullable (C# コンパイラ オプション)

**-nullable** オプションを使用すると、必要な Null 許容コンテキストを指定できます。

## <a name="syntax"></a>構文

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>引数

`+` &#124; `-`  
`+`、または単に **-nullable** を指定すると、コンパイラによって Null 許容のコンテキストが有効になります。 **nullable** を指定しない場合に有効な `-` を指定すると、Null 許容コンテキストは無効になります。

`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`  
Null 許容コンテキスト オプションを指定します。 有効または無効にする `+` または `-` に似ていますが、Null 許容のコンテキストをより細かく指定できます。 `enable` 引数は、 **-nullable** の指定と同じですが、Null 許容のコンテキストを有効にします。 `disable` を指定すると、Null 許容コンテキストは無効になります。 **nullable: warning** のように `warnings` 引数を指定すると、Null 許容の警告コンテキストが有効になります。 **-nullable:annotations** のように `annotations` 引数を指定すると、Null 許容の注釈コンテキストが有効になります。

## <a name="remarks"></a>Remarks

フロー分析は、実行可能コード内の変数に null 値が許容されるかどうかを推測するために使用します。 null 値が変数で許容されるかの推定は、変数の宣言されている null 許容とは無関係です。 メソッド呼び出しは、条件付きで省略される場合でも分析されます。 たとえば、リリース モードの <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> です。

次の属性の注釈が付いたメソッド呼び出しも、フロー分析に影響します。

- 単純な実行前条件: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> と <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- 単純な実行後条件: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> と <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- 条件付きの実行後条件: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> および <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (例: <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 用の `DoesNotReturnIf(false)`) と <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- メンバーの実行後条件: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> と <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>プロジェクトでこのコンパイラ オプションを設定するには

*.csproj* を編集して、`Project/PropertyGroup` 階層に `<Nullable>` タグを追加します。

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](./index.md)
- [Null 許容参照型](../../nullable-references.md)
