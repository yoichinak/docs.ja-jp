---
title: x:FieldModifier ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: c20564bcf8a25b1b59887fbefe6419671e0d6c03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971874"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier ディレクティブ
名前付きオブジェクトの参照フィールドが定義されているように、XAML のコンパイルの動作を変更します<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>へのアクセスの代わりに、<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>既定の動作。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*Public*|正確な文字列の指定に渡す<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は使用する分離コードのプログラミング言語によって異なります。 「解説」を参照してください。|  
  
## <a name="dependencies"></a>依存関係  
 XAML の運用環境で使用する場合`x:FieldModifier`どこでも、その XAML 運用環境のルート要素を宣言する必要があります、 [X:class ディレクティブ](x-class-directive.md)します。  
  
## <a name="remarks"></a>Remarks  
 `x:FieldModifier` クラスまたはそのメンバーの一般的なアクセス レベルを宣言するのには関係ありません。 XAML の運用環境の一部である、特定の XAML オブジェクトが処理され、アプリケーションのオブジェクト グラフにアクセス可能であるオブジェクトになりますが XAML 処理の動作にのみ関連します。 既定では、このようなオブジェクトのフィールド参照は厳重に保管され、コントロールのコンシューマーは、オブジェクト グラフを直接変更できなきます。 代わりに、コントロールのコンシューマーは、レイアウトのルートの子要素のコレクション、専用のパブリック プロパティを取得することによってなどのプログラミング モデル、によって実現される標準のパターンを使用して、オブジェクト グラフを変更する必要があり、具合です。  
  
 値、`x:FieldModifier`属性は、プログラミング言語によって異なるし、特定のフレームワークでの目的が異なることができます。 使用する文字列は、各言語の実装に依存、<xref:System.CodeDom.Compiler.CodeDomProvider>よぶ型コンバーターを返しますの意味を定義する<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>、その言語が、大文字小文字を区別するかどうか。  
  
- C# の場合、文字列を指定する渡す<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は`public`します。  
  
- Microsoft Visual Basic .net の指定に渡す文字列<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は`Public`します。  
  
- [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]XAML のターゲットを現在存在しません。 以外に渡す文字列が定義されているため、します。  
  
 指定することも<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>(`internal`でC#、 `Friend` Visual Basic で) が指定する<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>通常でないため、`NotPublic`動作は、既定では既に。  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> XAML が作成した要素へのアクセスを XAML がコンパイルされるアセンブリの外側のコードが必要があることを頻繁にではないために、既定の動作です。 具体的に設定していない場合は、XAML のコンパイル動作と WPF のセキュリティ アーキテクチャに、public 要素のインスタンスを格納するフィールドは宣言しません、`x:FieldModifier`パブリック アクセスを許可します。  
  
 `x:FieldModifier` のみを持つ要素の関係、 [X:name ディレクティブ](x-name-directive.md)その名前がパブリックになった後にフィールドを参照に使用されるためです。  
  
 既定では、ルート要素の部分クラスはパブリックです。ただし、行うことができます、非公開を使用して、 [X:classmodifier ディレクティブ](x-classmodifier-directive.md)します。 [X:classmodifier ディレクティブ](x-classmodifier-directive.md)ルート要素クラスのインスタンスのアクセス レベルにも影響します。 両方を配置できる`x:Name`と`x:FieldModifier`ルートに要素が、これだけパブリック フィールドのコピーを作成真のルート要素クラスのアクセス レベルも、ルート要素によって制御される[X:classmodifier ディレクティブ](x-classmodifier-directive.md)。  
  
## <a name="see-also"></a>関連項目

- [WPF における XAML とカスタム クラス](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [WPF における分離コードと XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name ディレクティブ](x-name-directive.md)
- [WPF アプリケーション (WPF) のビルド](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier ディレクティブ](x-classmodifier-directive.md)
