---
title: 型 '<typename>' が定義されていません。
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: c2675d61307d92da1710368668f43af3559060a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825041"
---
# <a name="type-typename-is-not-defined"></a>型 '\<typename >' が定義されていません
ステートメントは定義されていない型への参照をされています。 などの宣言ステートメントで型を定義できる`Enum`、 `Structure`、 `Class`、または`Interface`します。  
  
 **エラー ID:** BC30002  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   型の定義とその参照の両方で同じスペル チェックを使用していることを確認します。  
  
-   型定義が参照にアクセスできることを確認します。 たとえば、種類別のモジュールし、は宣言されています`Private`、型定義を参照しているモジュールに移動または宣言`Public`します。  
  
-   型の名前空間がプロジェクト内で再定義されていないことを確認します。 場合を使用して、`Global`完全型名を修飾するキーワード。 たとえば、プロジェクトに名前空間が定義されている場合`System`、<xref:System.Object?displayProperty=nameWithType>で完全修飾である場合を除き、型にアクセスできません、`Global`キーワード:`Global.System.Object`します。  
  
-   型が定義されている場合、オブジェクト ライブラリまたはタイプ ライブラリが定義されているが、Visual Basic、クリックに登録されていない場合**参照の追加**上、**プロジェクト**メニューのおよび適切なオブジェクトを選択ライブラリまたはタイプ ライブラリ。  
  
-   型が対象となる .NET Framework プロファイルの一部であるアセンブリであることを確認します。 詳細については、「[.NET Framework を対象とするエラーのトラブルシューティング](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
