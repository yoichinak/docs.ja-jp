---
title: 関数型変換 (Visual Basic) の適用性
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: 1903a59ec666c7d0b4c585abe5424cc1a0fd902d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642420"
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>関数型変換 (Visual Basic) の適用性
純粋関数型変換は、さまざまな状況で適用できます。  
  
 関数型変換の方法は、構造化されたデータのクエリと操作に適しているため、LINQ テクノロジに適切に対応できます。 ただし、関数型変換の適用範囲は、LINQ で使用する場合に比べてはるかに広範です。 データ形式の変換を中心とする処理はすべて、関数型変換の適用対象と考えることができます。  
  
 この方法は、一見して適用対象とは思われない数多くの問題に適用できます。 次に示す適用対象では、関数型変換を LINQ と組み合わせて、または切り離して使用することを検討する必要があります。  
  
- XML ベースのドキュメント。 XML 言語の整形式データは、関数型変換を通じて容易に操作できます。 詳細については、次を参照してください。[変換 XML の関数型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)します。  
  
- その他の構造化されたファイル形式。 Windows.ini ファイルからプレーンテキストのドキュメントに至るほとんどのファイルは、分析や変換に適した構造を備えています。  
  
- データ ストリーミング プロトコル。 通信プロトコルへのデータのエンコードおよび通信プロトコルからのデータのデコードは、単純な関数型変換で表せる場合がほとんどです。  
  
- RDBMS データと OODBMS データ。 リレーショナル データベースおよびオブジェクト指向データベースは、構造化されたデータ ソースとして XML と同様に広く使用されています。  
  
- 数学的、統計的、および科学的なソリューション。 これらの分野では、視覚化、予測、重要な問題の解決などを支援する際に、大きなデータ セットが操作される傾向があります。  
  
 」の説明に従って[純粋に戻った関数にリファクタリング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)、純粋関数を使用して、関数型プログラミングの例を示します。 純粋関数は、その直接的な利点に加えて、関数型変換の観点から問題について考える場合に役立ちます。 この方法は、プログラムおよびクラスの設計にも大きな影響を与えます。 上に示したように、問題がデータ変換ソリューションに関連している場合は、特に影響を受けます。  
  
 このチュートリアルでは扱いませんが、関数型変換の観点から影響を受ける設計は、アクターとしてオブジェクトよりもプロセスに重点を置く傾向があり、その結果であるソリューションは、個別のオブジェクト状態変更ではなく一連の大規模な変換として実装される傾向にあります。  
  
 ここでも、Visual Basic に命令型と機能の両方のアプローチがサポートされているので、両方の要素を組み込むことが、アプリケーションの最適なデザインことに注意してください。  
  
## <a name="see-also"></a>関連項目

- [純粋関数型変換 (Visual Basic) の概要](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [XML の関数型変換 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)
- [純粋関数 (Visual Basic) へのリファクタリング](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
