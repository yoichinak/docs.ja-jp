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
ms.openlocfilehash: 3eca756429c5fec8f324a17350844b59baf9ccf7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586260"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic における Me、My、MyBase、MyClass
`Me`、 `My`、 `MyBase`、および`MyClass`Visual Basic で名前は似ていますが、さまざまな目的があります。 このトピックでは、それらを区別するために、これらのエンティティの各をについて説明します。  
  
## <a name="me"></a>Me  
 `Me`キーワードはクラスまたは構造体の現在のコードが実行されているは、特定のインスタンスを参照する方法を提供します。 `Me` オブジェクト変数または構造体変数を参照する現在のインスタンスのいずれかのように動作します。 使用して`Me`はクラスまたは構造体の現在実行中のインスタンスに関する情報を別のクラス、構造体、またはモジュール内のプロシージャに渡すために特に便利です。  
  
 たとえば、モジュールに、次の手順があるとします。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 このプロシージャを呼び出すしの現在のインスタンスを渡すことができます、<xref:System.Windows.Forms.Form>クラスを次のステートメントを使用して、引数として。  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 `My`機能が多数のコンピューター、アプリケーション、設定、リソースとやり取りする Visual Basic のユーザーを有効にすると、.NET Framework クラスを簡単かつ直感的なアクセスを提供します。  
  
## <a name="mybase"></a>MyBase  
 `MyBase`キーワードはクラスの現在のインスタンスの基本クラスを参照するオブジェクト変数のように動作します。 `MyBase` 通常オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーへのアクセスに使用されます。 `MyBase.New` 派生クラスのコンス トラクターから基本クラスのコンス トラクターを明示的に呼び出すに使用されます。  
  
## <a name="myclass"></a>MyClass  
 `MyClass`キーワードが最初に実装されているクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass` ような`Me`、上のすべてのメソッド呼び出しとして扱われます、メソッドしますが、`NotOverridable`します。  
  
## <a name="see-also"></a>関連項目

- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
