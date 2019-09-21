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
ms.openlocfilehash: 5daff0567c1b1415fe994f6e39b4079cb2ab7346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053819"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier ディレクティブ
が指定されて`x:Class`いる場合に XAML のコンパイル動作を変更します。 `class`具体的には、 `Public`アクセスレベル (既定値) を持つ部分を作成するのでは`x:Class`なく、 `NotPublic`指定されたがアクセスレベルで作成されます。 この動作は、生成されたアセンブリのクラスのアクセスレベルに影響します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*NotPublic*|を指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>するために渡す正確な文字列は、使用する分離コードプログラミング言語によって異なります。 「解説」を参照してください。|  
  
## <a name="dependencies"></a>依存関係  
 [x:Class](x-class-directive.md)も同じ要素に指定する必要があり、その要素はページのルート要素である必要があります。 詳細については、「 [ \[4.3.1.8\] 」セクション](https://go.microsoft.com/fwlink/?LinkId=114525)を参照してください。  
  
## <a name="remarks"></a>Remarks  
 .NET Framework XAML サービス`x:ClassModifier`の使用におけるの値は、プログラミング言語によって異なります。 使用する文字列は、各言語がを実装<xref:System.CodeDom.Compiler.CodeDomProvider>する方法、およびが返す型コンバーターによって異なります。これにより、との<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>意味が定義され、その言語で大文字と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>小文字が区別されるかどうかが決まります。  
  
- C#では、を指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>するために渡す`internal`文字列はです。  
  
- Microsoft Visual Basic .net の場合、指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>するために渡す文字列は`Friend`です。  
  
- /Cli C++では、XAML のコンパイルをサポートするターゲットは存在しません。したがって、渡す値は指定されていません。  
  
 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>を指定することも`public`できC#ます`Public` (in、Visual Basic)。ただし<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 、は、が<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>既に既定の動作であるため、を指定することはあまりありません。  
  
 `private`でC#は、入れ子になったクラス参照が XAML `x:ClassModifier` <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>でサポートされていないため、修飾子は同じ効果を持つため、ユーザーコードのアクセスレベルに関する同じ制限を持つその他の値は、には関係ありません.  
  
## <a name="security-notes"></a>セキュリティに関する注意事項  
 で`x:ClassModifier`宣言されているアクセスレベルは、特定のフレームワークとその機能によって解釈されることもあります。 Wpf に`x:ClassModifier`は、の型を読み込んでインスタンス`internal`化する機能が含まれています。これは、そのクラスが、パッケージ URI 参照を通じて WPF リソースから参照されている場合です。 このケースの結果として、他のフレームワークによって実装されている可能性が`x:ClassModifier`ある場合は、を排他的に使用して、可能なすべてのインスタンス化試行をブロックしないでください。  
  
## <a name="see-also"></a>関連項目

- [x:Class ディレクティブ](x-class-directive.md)
- [WPF における分離コードと XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier ディレクティブ](x-fieldmodifier-directive.md)
- [セキュリティ (WPF)](../wpf/security-wpf.md)
- [WPF から System.Xaml に移行した型](types-migrated-from-wpf-to-system-xaml.md)
