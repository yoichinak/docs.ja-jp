---
title: x:FieldModifier ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 646ad1ca99d83f9fb2994f3c394eca27a60c0eac
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484720"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier ディレクティブ
名前付きオブジェクト参照のフィールドが<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>既定の動作ではなくアクセスで定義されるように、XAML コンパイル動作を変更します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*Public*|を指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>するために渡す文字列は、使用される分離コードプログラミング言語によって異なります。 「解説」を参照してください。|  
  
## <a name="dependencies"></a>依存関係  
 Xaml の運用環境で`x:FieldModifier`任意の場所を使用する場合は、その xaml の運用環境のルート要素で[x:Class ディレクティブ](x-class-directive.md)を宣言する必要があります。  
  
## <a name="remarks"></a>Remarks  
 `x:FieldModifier`は、クラスまたはそのメンバーの一般アクセスレベルを宣言する場合には関係ありません。 Xaml の運用環境に含まれる特定の XAML オブジェクトが処理され、アプリケーションのオブジェクトグラフでアクセスできる可能性があるオブジェクトになる場合にのみ、XAML 処理の動作に関連します。 既定では、このようなオブジェクトのフィールド参照はプライベートに保持されるため、コントロールのコンシューマーがオブジェクトグラフを直接変更することはできません。 代わりに、コントロールコンシューマーは、レイアウトルート、子要素コレクション、専用のパブリックプロパティなどを取得することによって、プログラミングモデルによって有効になる標準パターンを使用して、オブジェクトグラフを変更する必要があります。  
  
 `x:FieldModifier`属性の値はプログラミング言語によって異なり、その目的は特定のフレームワークによって異なります。 使用する文字列は、各言語がを実装<xref:System.CodeDom.Compiler.CodeDomProvider>する方法、およびが返す型コンバーターによって異なります。これにより、との<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>意味が定義され、その言語で大文字と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>小文字が区別されるかどうかが決まります。  
  
- C#では、を指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>するために渡す`public`文字列はです。  
  
- Microsoft Visual Basic .net の場合、指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>するために渡す文字列は`Public`です。  
  
- /Cli C++の場合、現在 XAML のターゲットは存在しません。したがって、渡す文字列は定義されていません。  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ( <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `NotPublic`の Visual Basic場合`Friend`は) を指定することもできますが、動作は既に既定値であるため、を指定することはまれです。 C#`internal`  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は、XAML をコンパイルしたアセンブリの外部のコードが XAML で作成された要素にアクセスする必要があるため、既定の動作です。 WPF のセキュリティアーキテクチャは、パブリックアクセスを許可するように明示的に設定しない限り、XAML のコンパイル`x:FieldModifier`動作と共に、要素インスタンスをパブリックとして格納するフィールドを宣言しません。  
  
 `x:FieldModifier`は、public の後にフィールドを参照するために使用されるため、 [X:Name ディレクティブ](x-name-directive.md)を持つ要素にのみ関連します。  
  
 既定では、ルート要素の部分クラスは public です。ただし、 [X:ClassModifier ディレクティブ](x-classmodifier-directive.md)を使用してパブリックにすることはできません。 [X:ClassModifier ディレクティブ](x-classmodifier-directive.md)は、ルート要素クラスのインスタンスのアクセスレベルにも影響します。 ルート要素にと`x:Name` `x:FieldModifier`の両方を含めることができますが、これによってルート要素のパブリックフィールドコピーが作成されるだけで、 [x:ClassModifier ディレクティブ](x-classmodifier-directive.md)によって引き続き制御される true のルート要素クラスアクセスレベルが使用されます。  
  
## <a name="see-also"></a>関連項目

- [WPF における XAML とカスタム クラス](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [WPF における分離コードと XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name ディレクティブ](x-name-directive.md)
- [WPF アプリケーション (WPF) のビルド](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier ディレクティブ](x-classmodifier-directive.md)
