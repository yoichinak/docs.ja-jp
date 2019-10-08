---
title: Visual Basic における Me、My、MyBase、MyClass
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
ms.openlocfilehash: 7df146e09a1d7cd730f4cf539d6823f7ced44bd1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002533"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic における Me、My、MyBase、MyClass
`Me`、`My`、`MyBase`、および `MyClass` Visual Basic の名前は似ていますが、目的は異なります。 このトピックでは、これらの各エンティティについて説明します。  
  
## <a name="me"></a>Me  
 @No__t-0 キーワードは、コードが現在実行されているクラスまたは構造体の特定のインスタンスを参照する手段を提供します。 `Me` は、オブジェクト変数または現在のインスタンスを参照する構造体変数のように動作します。 @No__t-0 を使用すると、クラスまたは構造体の現在実行中のインスタンスに関する情報を、別のクラス、構造体、またはモジュール内のプロシージャに渡す場合に特に便利です。  
  
 たとえば、モジュールに次のプロシージャがあるとします。  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 次のステートメントを使用して、このプロシージャを呼び出して、<xref:System.Windows.Forms.Form> クラスの現在のインスタンスを引数として渡すことができます。  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 @No__t 0 の機能を使用すると、さまざまな .NET Framework クラスに簡単かつ直感的にアクセスできるので、Visual Basic ユーザーは、コンピューター、アプリケーション、設定、リソースなどと対話できます。  
  
## <a name="mybase"></a>MyBase  
 @No__t-0 キーワードは、クラスの現在のインスタンスの基底クラスを参照するオブジェクト変数のように動作します。 `MyBase` は、派生クラスでオーバーライドまたはシャドウされる基底クラスのメンバーにアクセスするためによく使用されます。 `MyBase.New` は、派生クラスのコンストラクターから基底クラスのコンストラクターを明示的に呼び出すために使用されます。  
  
## <a name="myclass"></a>MyClass  
 @No__t-0 キーワードは、もともと実装されているクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass` は `Me` に似ていますが、このメソッドのすべてのメソッド呼び出しは、メソッドが @no__t であるかのように処理されます。  
  
## <a name="see-also"></a>関連項目

- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
