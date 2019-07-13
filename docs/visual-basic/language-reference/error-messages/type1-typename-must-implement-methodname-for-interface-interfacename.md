---
title: <type1>'<typename>'実装する必要があります'<methodname>'interface' の<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013609"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 >'\<typename >' を実装する必要があります '\<methodname >' のインターフェイス'\<interfacename >'
クラスまたは構造体がインターフェイスを実装するために要求しているインターフェイスによって定義されたプロシージャを実装していません。 インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **エラー ID:** BC30149  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 同じ名前と、インターフェイスで定義されたシグネチャを持つプロシージャを宣言します。 必ず含めて、少なくとも`End Function`または`End Sub`ステートメント。  
  
2. 追加、`Implements`句の末尾に、`Function`または`Sub`ステートメント。 例えば:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>関連項目

- [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)
- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
