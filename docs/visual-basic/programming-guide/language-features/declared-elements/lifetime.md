---
title: Visual Basic における有効期間
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 7a8730834c5241ddb1271d689cdda8942741f15f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824924"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic における有効期間
*有効期間*宣言された要素は、一定期間その中に、使用可能です。 変数は、有効期間を持つ要素ののみです。 このため、コンパイラは、プロシージャのパラメーターと変数の特殊なケースとして関数を返します。 変数の有効期間は、値を保持できる期間を表します。 その有効期間、その値を変更できますが、いくつかの値を常に保持します。  
  
## <a name="different-lifetimes"></a>別の有効期間  
 A*メンバー変数*(プロシージャの外側のモジュール レベルで宣言された) 通常が宣言されている要素と同じ有効期間があります。 クラスまたは構造体が宣言されているインスタンスごとに個別のコピーとしてクラスまたは構造体で宣言された非共有変数が存在します。 このような各変数には、そのインスタンスと同じ有効期間があります。 ただし、`Shared`変数が有効期間は 1 つだけで、アプリケーションの実行全体の時間が続きます。  
  
 A*ローカル変数*(プロシージャの内部で宣言) が宣言されている手順を実行中にのみ存在します。 関数の戻り値とそのプロシージャのパラメーターにも当てはまります。 ただし、そのプロシージャの他のプロシージャを呼び出した場合は、呼び出されたプロシージャが実行中にローカル変数の値は保持します。  
  
## <a name="beginning-of-lifetime"></a>有効期間の開始  
 ローカル変数の有効期間は、コントロールが宣言されている手順に入ったときに開始します。 プロシージャが開始されるとすぐにそのデータ型の既定値にすべてのローカル変数が初期化されて実行されています。 プロシージャが検出した場合、`Dim`初期値を指定するステートメントでは、変数が設定、これらの値をコードが、それらを他の値を既に割り当てられている場合でもです。  
  
 構造体変数の各メンバーは、別個の変数の場合と同様に初期化されます。 同様に、配列変数の各要素は、個別に初期化されます。  
  
 プロシージャ内のブロック内で宣言された変数 (など、`For`ループ)、プロシージャへのエントリで初期化されます。 これらの初期化は、コードが実行されるか、ブロックするかどうかよりも反映されます。  
  
## <a name="end-of-lifetime"></a>有効期間の終了  
 プロシージャが終了すると、ローカル変数の値は保持されず、Visual Basic のメモリを解放します。 次回、プロシージャを呼び出すすべてのローカル変数が新しく作成され再初期化します。  
  
 クラスまたは構造体のインスタンスが終了すると、非共有変数には、メモリとその値が失われます。 クラスまたは構造体の新しいインスタンスごとでは、作成し、非共有変数を再初期化します。 ただし、`Shared`変数は、アプリケーションの実行が停止されるまで保持されます。  
  
## <a name="extension-of-lifetime"></a>有効期間の延長  
 ローカル変数を宣言する場合、`Static`キーワード、その有効期間がそのプロシージャの実行時間よりも長くなります。 次の表は、プロシージャの宣言がどのくらいの期間を決定する方法、`Static`変数が存在します。  
  
|プロシージャの場所との共有|静的変数の有効期間を開始します。|静的変数の有効期間の終了|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|(既定では共有) モジュールで|最初に、プロシージャを呼び出す|アプリケーションの実行が終了|  
|クラスでは、 `Shared` (手順はインスタンス メンバーではありません)|最初に、特定のインスタンスまたはクラスまたは構造体名自体のいずれかの手順が呼び出されます|アプリケーションの実行が終了|  
|クラスのインスタンスでない`Shared`(プロシージャではインスタンス メンバー)|最初に、プロシージャは特定のインスタンスで呼び出されます。|ガベージ コレクション (GC) のインスタンスを解放する場合|  
  
## <a name="static-variables-of-the-same-name"></a>同じ名前の静的変数  
 1 つ以上の手順で同じ名前を持つ静的変数を宣言することができます。 これを行うと、Visual Basic コンパイラはこのような各変数は別々 の要素を考慮します。 これらの変数のいずれかの初期化では、他の値は影響しません。 同じには、一連のオーバー ロードのプロシージャを定義および各オーバー ロード内の同じ名前を持つ静的変数を宣言する場合が適用されます。  
  
## <a name="containing-elements-for-static-variables"></a>静的変数の要素を含む  
 つまり、そのクラスのプロシージャの中、クラス内の静的ローカル変数を宣言できます。 ただし、構造体のメンバー、またはその構造内のプロシージャのローカル変数として、構造体の静的ローカル変数を宣言することはできません。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例で変数を宣言、[静的](../../../../visual-basic/language-reference/modifiers/static.md)キーワード。 (必要はありませんが、`Dim`キーワードと、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)などの修飾子を使用して`Static`)。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>コメント  
 前の例では、変数`applesSold`手順の後に残ります`runningTotal`呼び出し元のコードを返します。 次回`runningTotal`が呼び出され、`applesSold`以前に計算された値を保持します。  
  
 場合`applesSold`を使用せずに宣言されていた`Static`への呼び出しの間で、前の累積値を保持されませんが`runningTotal`します。 次回`runningTotal`が呼び出された`applesSold`はされて再作成され、0 に初期化と`runningTotal`が呼び出された同じの値は返さだけです。  
  
### <a name="compiling-the-code"></a>コードのコンパイル  
 宣言の一部として静的ローカル変数の値を初期化することができます。 配列を宣言する場合`Static`、そのランク (次元数)、各次元の長さと個々 の要素の値を初期化することができます。  
  
### <a name="security"></a>セキュリティ  
 前の例では、宣言することによって同じ有効期間を生成できます`applesSold`モジュール レベル。 この方法で変数のスコープを変更した場合ただし、プロシージャでに排他的にアクセスが必要なくなりましたがあります。 他のプロシージャにアクセスするため`applesSold`との値を変更、コードを維持するためにはより困難になることし、累計が信頼性が高くない可能性があります。  
  
## <a name="see-also"></a>関連項目

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
