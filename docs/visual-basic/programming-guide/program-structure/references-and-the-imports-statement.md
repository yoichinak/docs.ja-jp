---
title: 参照と Imports ステートメント (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: f3396eb3e758dc456d86de80246de24349680f2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967753"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>参照と Imports ステートメント (Visual Basic)
利用できる外部オブジェクト プロジェクトを選択して、**参照の追加**コマンドを**プロジェクト**メニュー。 Visual Basic での参照は、タイプ ライブラリの詳細に説明と似ていますが、アセンブリを指定できます。  
  
## <a name="the-imports-statement"></a>Imports ステートメント  
 アセンブリには、1 つまたは複数の名前空間が含まれます。 アセンブリへの参照を追加するときに追加することも、`Imports`ステートメント、モジュール内でそのアセンブリの名前空間の表示を制御するモジュールにします。 `Imports`ステートメントでは、スコープのコンテキストの一意の参照を指定するために必要な名前空間の部分のみを使用することができます。  
  
 `Imports`ステートメントには、次の構文。  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` インポートされた名前空間を参照するコード内で使用できる短い名前を参照します。 `Namespace` 名前空間のいずれかで使用可能なプロジェクト参照をプロジェクト内での定義、または以前を通じて`Imports`ステートメント。  
  
 モジュールは、任意の数を含めることができます`Imports`ステートメント。 後に現れる必要があります`Option`ステートメント、存在する場合、その他のコードの前にします。  
  
> [!NOTE]
>  プロジェクト参照とを混同しないでください、`Imports`ステートメントまたは`Declare`ステートメント。 プロジェクト参照は、Visual Basic プロジェクトで使用できるアセンブリ内のオブジェクトなど、外部のオブジェクトを作成します。 `Imports`ステートメントは、プロジェクト参照へのアクセスを簡略化が使用されますが、これらのオブジェクトへのアクセスを提供しません。 `Declare`ダイナミック リンク ライブラリ (DLL) で外部プロシージャへの参照を宣言するステートメントを使用します。  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports ステートメントを使用してエイリアスを使用します。  
 `Imports`ステートメントやすくクラスのアクセス方法によって明示的に参照の完全修飾名を入力する必要はありません。 エイリアスを使用して、名前空間の 1 つの部分にわかりやすい名前を割り当てできます。 などの一部は、複数の行に表示されるテキストの 1 つの原因となるシーケンスをフィード キャリッジ リターン/ライン、<xref:Microsoft.VisualBasic.ControlChars>でモジュール、<xref:Microsoft.VisualBasic?displayProperty=nameWithType>名前空間。 エイリアスなしのプログラムでこの定数を使用するには、次のコードを入力する必要があります。  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports` ステートメントがすぐに次のいずれかの最初の行を必ず`Option`モジュール内のステートメント。 次のコード フラグメントをインポートしてエイリアスを割り当てる方法を示しています、<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>モジュール。  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 この名前空間への今後の参照が大幅に短くできます。  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 場合、`Imports`ステートメントでは、エイリアス名を含まない、インポートされた名前空間内で定義されている要素を修飾なしのモジュールで使用できます。 エイリアス名が指定されている場合はでその名前空間内に含まれる名前の修飾子としてに使用する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [方法: コマンド ラインを使用してアセンブリを作成および使用する](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
