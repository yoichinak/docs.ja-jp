---
title: この 'Sub New' の最初のステートメントは、'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません (パラメーターのないアクセス可能なコンストラクターがありません)。
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: d29d7609f8f3f38eadda9a9c763f3ba8e6b99e61
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365088"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>この 'Sub New' の最初のステートメントは、'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません (パラメーターのないアクセス可能なコンストラクターがありません)。
この 'Sub New' の最初のステートメントは 'mybase.new' または 'myclass.new' への呼び出しをする必要がありますので、基本クラスの\<basename >' の'\<derivedname >' 引数なしで呼び出せるアクセス可能な ' Sub New' はありません。  
  
 派生クラスでは、すべてのコンス トラクターが基底クラスのコンス トラクターを呼び出す必要があります (`MyBase.New`)。 基底クラスが派生クラスでアクセス可能なパラメーターなしのコンス トラクターを持つ場合`MyBase.New`自動的に呼び出すことができます。 できない場合は、パラメーターを持つ基底クラスのコンス トラクターを呼び出す必要があり、自動的に実行できません。 この場合、すべての派生クラス コンス トラクターの最初のステートメントは、基本クラスをパラメーター化されたコンス トラクターを呼び出すか、呼び出す基底クラスのコンス トラクターを派生クラスで別のコンス トラクターを呼び出す必要があります。  
  
 **エラー ID:** BC30148  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   いずれかの呼び出し`MyBase.New`、必要なパラメーターを指定するか、ピア コンス トラクターが、このような呼び出しを行います。  
  
     たとえば、基底クラスとして宣言されているコンス トラクターがある`Public Sub New(ByVal index as Integer)`、最初のステートメントで、派生クラスのコンス トラクターがあります`MyBase.New(100)`します。  
  
## <a name="see-also"></a>関連項目
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
