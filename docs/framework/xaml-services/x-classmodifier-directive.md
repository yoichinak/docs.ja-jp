---
title: x:ClassModifier ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: fdbc69634e86992e71cfccdc080829b6b45f963c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100930"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier ディレクティブ
XAML のコンパイルの動作を変更するときに`x:Class`も提供されます。 部分を作成する代わりに、具体的には、`class`を持つ、`Public`アクセス レベル (既定)、指定された`x:Class`で作成、`NotPublic`アクセス レベル。 この動作では、生成されたアセンブリ内のクラスのアクセス レベルに影響します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*NotPublic*|正確な文字列を指定して渡す<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>を使用する分離コードのプログラミング言語によって異なります。 「解説」を参照してください。|  
  
## <a name="dependencies"></a>依存関係  
 [X:class](x-class-directive.md)も同じ要素に提供される必要があり、その要素は、ページのルート要素である必要があります。 詳細については、次を参照してください。 [ \[MS XAML\]セクション 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525)します。  
  
## <a name="remarks"></a>Remarks  
 値`x:ClassModifier`.NET Framework XAML サービスの使用状況はプログラミング言語によって異なります。 使用する文字列は、各言語の実装に依存、<xref:System.CodeDom.Compiler.CodeDomProvider>よぶ型コンバーターを返しますの意味を定義する<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>、その言語が、大文字小文字を区別するかどうか。  
  
-   C# の場合、文字列を指定する渡す<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は`internal`します。  
  
-   Microsoft Visual Basic .net の指定に渡す文字列<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は`Friend`します。  
  
-   [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]ターゲットをサポートする XAML をコンパイルするが存在しない; そのため、に渡す値は指定されていません。  
  
 指定することも<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>(`public` c# で`Public`Visual Basic で)。 ただし、を指定する<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>ために頻繁に行われます<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>が既に既定の動作。  
  
 対応するユーザー コードでは、その他の値へのアクセス レベルの制限など`private`c# では関連しない`x:ClassModifier`、XAML では、入れ子になったクラスの参照はサポートされていないため、それによって、<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修飾子のと同じ効果します。  
  
## <a name="security-notes"></a>セキュリティに関する注意事項  
 アクセス レベルで宣言されている`x:ClassModifier`は特定のフレームワークとその機能によって解釈される可能性があります。 WPF に読み込むし、型のインスタンスを作成する機能が含まれています、`x:ClassModifier`は`internal`pack URI 参照を使用して、WPF リソースからそのクラスが参照されている場合、します。 この場合、可能性のある他のフレームワークによって実装されるような結果、管理者はで排他的に依存しない`x:ClassModifier`使用可能なすべてのインスタンス化をブロックしようとします。  
  
## <a name="see-also"></a>関連項目

- [x:Class ディレクティブ](x-class-directive.md)
- [WPF における分離コードと XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier ディレクティブ](x-fieldmodifier-directive.md)
- [セキュリティ (WPF)](../wpf/security-wpf.md)
- [WPF から System.Xaml に移行した型](types-migrated-from-wpf-to-system-xaml.md)
