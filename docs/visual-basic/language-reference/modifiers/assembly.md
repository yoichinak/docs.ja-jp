---
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 1385919a1205a60104125fff1bdd24f409a091df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351648"
---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
ソース ファイルの先頭の属性がアセンブリ全体に適用されることを指定します。  
  
## <a name="remarks"></a>Remarks  
 クラスやプロパティなど、多くの属性が個々のプログラミング要素に関連しています。 そのような属性を適用するには、山かっこ (`< >`) 内の属性ブロックを宣言ステートメントに直接アタッチします。  
  
 属性が次の要素だけでなく、アセンブリ全体に関連する場合は、属性ブロックをソース ファイルの先頭に配置し、`Assembly` キーワードで属性を識別します。 それを現在のアセンブリ モジュールに適用する場合、[Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) キーワードを使用します。  
  
 また、AssemblyInfo.vb ファイル内のアセンブリに属性を適用することもできます。この場合、メイン ソースコード ファイルで属性ブロックを使用する必要はありません。  
  
## <a name="see-also"></a>関連項目

- [Module \<キーワード>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
