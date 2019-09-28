---
title: メンバーのオーバーロード
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: KrzysztofCwalina
ms.openlocfilehash: 4caa0ae78d168b23fd2862153bef0e3960d3ea42
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392948"
---
# <a name="member-overloading"></a>メンバーのオーバーロード
メンバーのオーバーロードとは、同じ型に複数のメンバーを作成し、パラメーターの数または型だけではなく、同じ名前を持つことを意味します。 たとえば、次の例では、`WriteLine` メソッドがオーバーロードされています。  
  
```csharp  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 パラメーターを持つことができるのはメソッド、コンストラクター、およびインデックス付きプロパティだけなので、これらのメンバーのみをオーバーロードできます。  
  
 オーバーロードは、再利用可能なライブラリのユーザビリティ、生産性、および読みやすさを向上させるための最も重要な手法の1つです。 パラメーターの数をオーバーロードすることで、コンストラクターとメソッドのより単純なバージョンを提供できるようになります。 パラメーターの型をオーバーロードすると、選択した異なる型のセットに対して同じ操作を実行するメンバーに対して同じメンバー名を使用できるようになります。  
  
 **✓ DO** 短いオーバー ロードで使用される既定値を示すためにわかりやすいパラメーター名を使用しようとしています。  
  
 **X AVOID** オーバー ロードのパラメーター名は任意で変更します。 1つのオーバーロード内のパラメーターが、別のオーバーロード内のパラメーターと同じ入力を表している場合、パラメーターの名前は同じである必要があります。  
  
 **X AVOID** メンバーをオーバー ロードされているのパラメーターの順序で一貫していません。 同じ名前のパラメーターは、すべてのオーバーロードで同じ位置に出現します。  
  
 **✓ DO** (拡張機能が必要な場合)、最長のオーバー ロードだけの仮想を作成します。 より短いオーバーロードでは、より長いオーバーロードに対してを呼び出すだけで済みます。  
  
 **X DO NOT** 使用`ref`または`out`メンバーをオーバー ロードする修飾子です。  
  
 一部の言語では、このようなオーバーロードの呼び出しを解決できません。 また、通常、このようなオーバーロードには完全に異なるセマンティクスがあり、オーバーロードは使用できませんが、2つの異なるメソッドを使用することをお勧めします。  
  
 **X DO NOT** 同じ位置と類似した種類のパラメーターを使用してまだセマンティクスが異なるオーバー ロードがあります。  
  
 **✓ DO** 許可`null`省略可能な引数に渡されます。  
  
 **✓ DO** メンバーの既定の引数を持つメンバーを定義するのではなく、オーバー ロードを使用します。  
  
 既定の引数は CLS に準拠していません。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 [ Framework のデザインガイドラインから、ピアソン教育, Inc. のアクセス許可によって @no__t。再利用可能な .NET ライブラリの規則、表現、パターン、2番目のエディション @ no__t-0 by Krzysztof Cwalina、および Addison-Wesley Professional によって Microsoft Windows 開発シリーズの一部として2008年10月22日に公開さ @no__t れました。  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
