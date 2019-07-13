---
title: <type1>'<typename>'実装する必要があります'<membername>'interface' の<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 86b0d46e0e27b2fd8d1fccb37f4a3c45e95f5f63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792094"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 >'\<typename >' を実装する必要があります '\<membername >' のインターフェイス'\<interfacename >'
'\<typename >' を実装する必要があります'\<membername >' のインターフェイス '\<interfacename >'。 'ReadOnly' を持つプロパティを実装する/'WriteOnly' 指定子。  
  
 クラスまたは構造体、インターフェイスを実装する要求が、プロシージャ、プロパティ、またはインターフェイスで定義したイベントを実装しません。 インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **エラー ID:** BC30154  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 同じ名前と、インターフェイスで定義されたシグネチャを持つメンバーを宣言します。 必ず含めて、少なくとも`End Function`、 `End Sub`、または`End Property`ステートメント。  
  
2. 追加、`Implements`句の末尾に、 `Function`、 `Sub`、 `Property`、または`Event`ステートメント。 例:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. プロパティを実装する場合、以下のことを確認`ReadOnly`または`WriteOnly`インターフェイスの定義と同じ方法で使用されます。  
  
4. プロパティを実装する場合は、宣言`Get`と`Set`プロシージャに、必要に応じて。  
  
## <a name="see-also"></a>関連項目

- [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)
- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
