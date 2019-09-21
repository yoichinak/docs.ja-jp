---
title: x:Code 組み込み XAML 型
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 2b7713548b6269f079ef32b5bf1fe4fa630edcc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053792"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 組み込み XAML 型
XAML の実稼働環境内でのコードの配置を許可します。 このようなコードは、xaml をコンパイルする任意の XAML プロセッサの実装によってコンパイルすることも、ランタイムによる解釈など、後で使用できるように XAML の運用環境でコンパイルすることもできます。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Remarks  
 `x:Code` Xaml ディレクティブ要素内のコードは、通常の XML 名前空間と、指定された xaml 名前空間内で引き続き解釈されます。 そのため、通常は`x:Code` `CDATA`セグメント内で使用されるコードを囲む必要があります。  
  
 `x:Code`は、XAML 運用環境のすべての配置メカニズムで許可されていません。 特定のフレームワーク (WPF など) では、コードをコンパイルする必要があります。 他のフレームワークで`x:Code`は、一般に使用が禁止されている場合があります。  
  
 マネージ`x:Code`コンテンツを許可するフレームワークの場合、コンテンツに`x:Code`使用する正しい言語コンパイラは、アプリケーションのコンパイルに使用される、含んでいるプロジェクトの設定とターゲットによって決定されます。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 WPF で`x:Code`宣言されたコードには、いくつかの注目すべき制限があります。  
  
- `x:Code`ディレクティブ要素は、XAML 運用のルート要素の直接の子要素である必要があります。  
  
- [X:Class ディレクティブ](x-class-directive.md)は、親ルート要素で指定する必要があります。  
  
- 内`x:Code`に配置されたコードは、その XAML ページ用に既に作成されている部分クラスのスコープ内になるように、コンパイルによって処理されます。 したがって、定義するすべてのコードは、その部分クラスのメンバーまたは変数である必要があります。  
  
- クラスを部分クラス内に入れ子にする以外に、追加のクラスを定義することはできません (入れ子にすることはできますが、入れ子になったクラスは XAML で参照できないため、一般的ではありません)。 既存の部分クラスに使用されている名前空間以外の CLR 名前空間を定義したり、に追加したりすることはできません。  
  
- 部分クラスの CLR 名前空間の外部にあるコードエンティティへの参照はすべて、完全修飾されている必要があります。 宣言されるメンバーが部分クラスのオーバーライド可能なメンバーをオーバーライドする場合は、言語固有の override キーワードを使用して指定する必要があります。 スコープ内で`x:Code`宣言されたメンバーが xaml から作成された部分クラスのメンバーと競合する場合、コンパイラが競合を報告する方法では、xaml ファイルをコンパイルまたは読み込むことができません。  
  
## <a name="see-also"></a>関連項目

- [x:Class ディレクティブ](x-class-directive.md)
- [WPF における分離コードと XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
