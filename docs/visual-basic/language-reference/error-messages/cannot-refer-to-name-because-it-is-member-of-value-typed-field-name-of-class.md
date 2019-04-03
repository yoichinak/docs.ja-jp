---
title: "'<name>' は、'System.MarshalByRefObject' を基本クラスとして持つクラス '<name>' の値付きフィールド '<classname>' のメンバーであるため、参照できません。"
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: aac190119ced74496c4dd012d200fca6d895ff28
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826770"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>参照できません '\<名 >' の値に型指定されたフィールドのメンバーであるため、'\<名 >' のクラスの\<classname >' 'system.marshalbyrefobject'' 基底クラスとして
`System.MarshalByRefObject`クラスは、アプリケーション ドメイン境界を越えてオブジェクトへのリモート アクセスをサポートするアプリケーションを使用できます。 型を継承する必要があります、`MarshalByRejectObject`クラスの型がアプリケーション ドメイン境界を越えて使用するとします。 オブジェクトのメンバーが作成されたアプリケーション ドメインの外部で使用できないために、オブジェクトの状態はコピーされませんする必要があります。  
  
 **エラー ID:** BC30310  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  参照先のメンバーが有効かどうかを確認への参照を確認してください。  
  
2.  持つメンバーを明示的に修飾、`Me`キーワード。  
  
## <a name="see-also"></a>関連項目

- <xref:System.MarshalByRefObject>
- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
