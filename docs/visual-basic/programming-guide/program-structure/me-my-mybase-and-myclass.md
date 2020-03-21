---
title: Me、My、MyBase、および MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401431"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic における Me、My、MyBase、MyClass
`Me`、、、`My``MyBase`および`MyClass`、および Visual Basic では、似た名前が使用されますが、目的は異なります。 このトピックでは、これらのエンティティを区別するために、これらのエンティティについて説明します。  
  
## <a name="me"></a>自分  
 キーワード`Me`は、コードが現在実行されているクラスまたは構造体の特定のインスタンスを参照する方法を提供します。 `Me`オブジェクト変数または現在のインスタンスを参照する構造体変数と同じように動作します。 使用`Me`は、クラスまたは構造体の現在実行中のインスタンスに関する情報を別のクラス、構造体、またはモジュールのプロシージャに渡す場合に特に便利です。  
  
 たとえば、モジュールに次のプロシージャがあるとします。  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 このプロシージャを呼び出し、次のステートメントを<xref:System.Windows.Forms.Form>使用して、クラスの現在のインスタンスを引数として渡すことができます。  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 この`My`機能を使用すると、多数の .NET Framework クラスに簡単かつ直感的にアクセスでき、Visual Basic ユーザーはコンピュータ、アプリケーション、設定、リソースなどを操作できます。  
  
## <a name="mybase"></a>MyBase  
 キーワード`MyBase`は、クラスの現在のインスタンスの基本クラスを参照するオブジェクト変数のように動作します。 `MyBase`は、派生クラスでオーバーライドまたはシャドウされる基本クラスのメンバーにアクセスするためによく使用されます。 `MyBase.New`は、派生クラスのコンストラクターから基本クラスコンストラクターを明示的に呼び出すために使用します。  
  
## <a name="myclass"></a>MyClass  
 キーワード`MyClass`は、最初に実装されたクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass`は に`Me`似ていますが、メソッドのすべての呼び出しは、 メソッド`NotOverridable`と同じように扱われます。  
  
## <a name="see-also"></a>関連項目

- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
