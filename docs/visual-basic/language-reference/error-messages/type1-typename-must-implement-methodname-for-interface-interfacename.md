---
title: <type1>'<typename>' は、インターフェイス '<interfacename>' に対して '<methodname>' を実装しなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591592"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 > ' \< typename > ' は、インターフェイス ' 3interfacename @no__t ' に ' >-2methodname @no__t ' を実装しなければなりません
インターフェイスを実装するクラスまたは構造体が要求しますが、インターフェイスによって定義されたプロシージャは実装しません。 インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **エラー ID:** BC30149  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. インターフェイスで定義されているものと同じ名前およびシグネチャを持つプロシージャを宣言します。 少なくとも @no__t 0 または `End Sub` ステートメントを含めてください。  
  
2. @No__t-1 または `Sub` ステートメントの末尾に `Implements` 句を追加します。 以下に例を示します。  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>関連項目

- [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)
- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
