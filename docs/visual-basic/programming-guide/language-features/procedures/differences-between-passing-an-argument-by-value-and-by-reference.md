---
title: 引数の値渡しと参照渡しの違い (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 1b85941c14721280a5025db442c4793930244ec8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837513"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡しの違い (Visual Basic)
プロシージャに 1 つまたは複数の引数を渡すと、ときに、各引数は、呼び出し元のコード内の基になるプログラミング要素に対応します。 この基になる要素の値またはへの参照を渡すことができます。 これと呼ばれますが、*渡し*。  
  
## <a name="passing-by-value"></a>値渡し  
 引数を渡す*値によって*指定することによって、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャの定義に対応するパラメーターのキーワード。 この渡すメカニズムを使用して、Visual Basic は、プロシージャ内のローカル変数に基になるプログラミング要素の値をコピーします。 プロシージャのコードには、呼び出し元のコードで、基になる要素へのアクセスがありません。  
  
## <a name="passing-by-reference"></a>参照渡しで渡す  
 引数を渡す*参照によって*指定することによって、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)プロシージャの定義に対応するパラメーターのキーワード。 この渡すメカニズムを使用して、Visual Basic により、プロシージャ基になるプログラミング要素への直接参照では呼び出し元のコード。  
  
## <a name="passing-mechanism-and-element-type"></a>引き渡し方法および要素の型  
 渡す機能の選択は、基になる要素型の分類と同じではありません。 値渡しまたは参照によって渡すことは、プロシージャのコードを提供する Visual Basic を指します。 値型または参照型は、メモリ内プログラミング要素を格納する方法を参照します。  
  
 ただし、引き渡し方法および要素の型は相互にします。 参照型の値は、メモリ内の他の場所でのデータへのポインターです。 つまり、基になる要素自体にアクセスできない場合でも値渡しで参照型を渡すときにプロシージャ コードが、基になる要素のデータへのポインターを持っています。 たとえば、要素が、配列変数の場合は、プロシージャのコードでは、変数自体にアクセスできないが、配列メンバーにアクセスできます。  
  
## <a name="ability-to-modify"></a>変更する権限  
 変更不可能な要素は、引数として渡す、ときに、プロシージャ変更できません呼び出し元のコードで渡されるかどうか`ByVal`または`ByRef`します。  
  
 変更可能な要素では、次の表では、要素の型と渡し間の相互作用をまとめたものです。  
  
|要素型|渡されました。 `ByVal`|渡されました。 `ByRef`|  
|------------------|--------------------|--------------------|  
|値の型 (値のみを含む)|プロシージャには、変数、またはそのメンバーのいずれかを変更できません。|プロシージャには、変数とそのメンバーを変更できます。|  
|参照の型 (クラスまたは構造体のインスタンスへのポインターが含まれています)|プロシージャは、変数を変更することはできませんが、ポイントするインスタンスのメンバーを変更できます。|プロシージャには、変数と、ポイントするインスタンスのメンバーを変更できます。|  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)
- [方法: プロシージャ引数の値が変化しません。](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [方法: 引数の値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
