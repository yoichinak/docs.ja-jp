---
title: Visual Basic のプロパティと変数の違い
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: de4800e23519c2cc1c8b2b219287b9fa018b9bbf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842903"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic のプロパティと変数の違い
変数とプロパティは、アクセス可能な値を表します。 ただし、ストレージと実装の違いがあります。  
  
## <a name="variables"></a>変数  
 A*変数*メモリ位置に直接対応しています。 1 つの宣言ステートメントで変数を定義するとします。 変数、*ローカル変数*、プロシージャ内にあると、そのプロシージャ内でのみ使用可能な定義またはことができます、*メンバー変数*、いずれかの内部ではなく、モジュール、クラスまたは構造体で定義されています。プロシージャです。 メンバー変数とも呼ばれますが、*フィールド*します。  
  
## <a name="properties"></a>プロパティ  
 A*プロパティ*はモジュール、クラスまたは構造体で定義されているデータ要素です。 コード ブロックの間でのプロパティを定義する、`Property`と`End Property`ステートメント。 コード ブロックが含まれる、`Get`プロシージャ、`Set`プロシージャ、または両方。 これらのプロシージャ*プロパティ プロシージャ*または*プロパティ アクセサー*します。 取得するか、プロパティの値を格納するだけでなく、アクセス カウンターの更新などのカスタム アクションを実行することもできます。  
  
## <a name="differences"></a>相違点  
 次の表では、変数とプロパティのいくつかの重要な違いを示します。  
  
|相違点のポイント|変数|プロパティ|  
|-------------------------|--------------|--------------|  
|宣言|1 つの宣言ステートメント|一連のコード ブロック内のステートメント|  
|実装|1 つのストレージの場所|実行可能コード (プロパティ プロシージャ)|  
|記憶域|変数の値に直接関連付けられています。|通常、プロパティの親クラスまたはモジュールの外部からアクセスできない内部ストレージには<br /><br /> プロパティの値の可能性がありますまたは格納された要素として存在していない可能性があります<sup>1</sup>|  
|実行可能コード|なし|少なくとも 1 つの手順があります。|  
|読み取り/書き込みアクセス|読み取り/書き込みまたは読み取り専用|読み取り/書き込み、読み取り専用または書き込み専用|  
|(値を返すことを許可または) に加えて、カスタム アクション|無理です|設定またはプロパティの値を取得するの一部として実行できます。|  
  
 <sup>1</sup>変数とは異なり、プロパティの値は 1 つの項目の記憶域に直接対応しない可能性があります。 記憶域を利便性またはセキュリティに部分に分割する可能性がありますか、値は、暗号化された形式で格納される可能性があります。 このような場合、`Get`プロシージャはコンポーネントの編成または格納されている値の暗号化を解除し、`Set`プロシージャは新しい値を暗号化または構成の記憶域に分割することです。 プロパティ値があります、1 日の時間などの一時的な場合、`Get`プロシージャは計算こと、実行時にプロパティにアクセスするたびにします。  
  
## <a name="see-also"></a>関連項目

- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [方法: プロパティを作成します。](./how-to-create-a-property.md)
- [方法: 混合アクセス レベルを持つプロパティを宣言します。](./how-to-declare-a-property-with-mixed-access-levels.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)
- [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md)
