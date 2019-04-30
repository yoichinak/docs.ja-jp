---
title: 'x:Code 組み込み XAML 型 '
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
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971848"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 組み込み XAML 型 
XAML の運用環境でコードを配置をできます。 XAML、またはランタイムによって解釈など、後から使用の XAML の運用環境で左側をコンパイルする任意の XAML プロセッサ実装によってこのようなコードをコンパイルすることができますか。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Remarks  
 内のコード、 `x:Code` XAML ディレクティブ要素は、一般的な XML 名前空間内で解釈のままと XAML 名前空間を提供します。 したがって、用のコードを囲むために必要な通常は`x:Code`内で、`CDATA`セグメント。  
  
 `x:Code` XAML の運用環境のすべての可能な展開メカニズムは許可されません。 特定のフレームワーク (WPF など) では、コードをコンパイルする必要があります。 その他のフレームワークで`x:Code`使用状況を通常許可されない可能性があります。  
  
 管理を許可するフレームワーク`x:Code`コンテンツに使用する適切な言語コンパイラ`x:Code`コンテンツが設定およびアプリケーションをコンパイルするために使用を含むプロジェクトのターゲットによって決定されます。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 内で宣言されているコード`x:Code`は WPF がいくつかの注目すべき制限があります。  
  
- `x:Code`ディレクティブ要素は XAML の運用環境のルート要素の直接の子要素である必要があります。  
  
- [X:class ディレクティブ](x-class-directive.md)親ルート要素に提供する必要があります。  
  
- コード内に配置`x:Code`は、その XAML ページを既に作成されている部分クラスのスコープ内にあるコンパイルで扱われます。 したがってすべてのコードを定義するには、その部分クラスのメンバーまたは変数があります。  
  
- 部分クラス内にクラスを入れ子にして他よりも、追加のクラスを定義することはできません (入れ子が許可されているが、XAML で入れ子になったクラスは参照できないために、通常ではありません)。 既存の部分クラスに使用される名前空間以外の CLR 名前空間を定義またはに追加できません。  
  
- 部分クラスの CLR 名前空間の外部のコード エンティティを参照する必要がありますすべて完全修飾します。 部分クラスのオーバーライド可能なメンバーをオーバーライド メンバーが宣言されている場合は、これを言語固有の override キーワードを指定する必要があります。 メンバーが宣言されている場合`x:Code`XAML から作成された部分クラスのメンバーと競合するスコープ、このような方法で、コンパイラが、競合を報告する XAML ファイルことはできませんコンパイルまたは読み込みます。  
  
## <a name="see-also"></a>関連項目

- [x:Class ディレクティブ](x-class-directive.md)
- [WPF における分離コードと XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
