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
ms.openlocfilehash: b13f9e1551aec7e53ba1ac2ed0b9049d46b0a756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945546"
---
# <a name="member-overloading"></a>メンバーのオーバーロード
メンバーのオーバー ロードでは、数またはのパラメーターの型でのみ異なるが、同じ名前を持つ同じ型に 2 つ以上のメンバーの作成を意味します。 たとえば、以下では、`WriteLine`メソッドがオーバー ロードします。  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 メソッド、コンス トラクター、およびインデックス付きプロパティは、パラメーターを持つことができます、ため、これらのメンバーだけがオーバー ロードできます。  
  
 オーバー ロードでは、使いやすさ、生産性、および再利用可能なライブラリの読みやすさを向上させるための最も重要な手法の 1 つです。 パラメーターの数のオーバー ロードできるようになりますコンス トラクターとメソッドの単純なバージョンを提供します。 パラメーターの型のオーバー ロードできるようになります同じメンバーの選択したさまざまな種類のセットで同じ操作を実行する名前を使用します。  
  
 **✓ DO** 短いオーバー ロードで使用される既定値を示すためにわかりやすいパラメーター名を使用しようとしています。  
  
 **X AVOID** オーバー ロードのパラメーター名は任意で変更します。 1 つのオーバー ロードのパラメーターは、別のオーバー ロードのパラメーターとして、同じ入力を表している場合、パラメーターは、同じ名前が必要です。  
  
 **X AVOID** メンバーをオーバー ロードされているのパラメーターの順序で一貫していません。 同じ名前のパラメーターは、すべてのオーバー ロード内の同じ位置に表示されます。  
  
 **✓ DO** (拡張機能が必要な場合)、最長のオーバー ロードだけの仮想を作成します。 短いオーバー ロードは、長いオーバー ロードに単にを通じてを呼び出す必要があります。  
  
 **X DO NOT** 使用`ref`または`out`メンバーをオーバー ロードする修飾子です。  
  
 一部の言語では、このようなオーバー ロードの呼び出しを解決できません。 さらに、このようなオーバー ロード、通常は完全に異なるセマンティクスを持つ可能性がありますされないをオーバー ロードが 2 つの個別のメソッド代わりにします。  
  
 **X DO NOT** 同じ位置と類似した種類のパラメーターを使用してまだセマンティクスが異なるオーバー ロードがあります。  
  
 **✓ DO** 許可`null`省略可能な引数に渡されます。  
  
 **✓ DO** メンバーの既定の引数を持つメンバーを定義するのではなく、オーバー ロードを使用します。  
  
 既定の引数は、CLS 準拠ではありません。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
