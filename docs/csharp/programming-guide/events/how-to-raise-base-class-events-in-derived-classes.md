---
title: '方法: 派生クラスから基本クラス イベントを発生させる - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 820bdcb895a1c3eb7c56db55b298c1a9636f2f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921878"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>方法: 派生クラスから基本クラス イベントを発生させる (C# プログラミング ガイド)
ここでは単純な例を使用し、派生クラスからも発生させることができるように基底クラスでイベントを宣言する標準的な方法について説明します。 このパターンは、.NET Framework クラス ライブラリの Windows フォーム クラスで広く使用されています。  
  
 他のクラスの基底クラスとして使用できるクラスを作成するときは、イベントは宣言元のクラス内からしか呼び出せない特別な種類のデリゲートであることを考慮する必要があります。 派生クラスは、基底クラスの中で宣言されたイベントを直接呼び出せません。 常に基底クラスからイベントを発生させるようにすると便利な場合もありますが、ほとんどの場合、派生クラスで基底クラス イベントを呼び出せるようにするべきです。 そのために、イベントをラップする基底クラスで、保護された呼び出しメソッドを作成できます。 この呼び出しメソッドを呼び出すかオーバーライドすることによって、派生クラスから間接的にイベントを呼び出すことができます。  
  
> [!NOTE]
> 基底クラスで仮想イベントを宣言したり、派生クラスでそれらをオーバーライドしたりしないでください。 C# コンパイラはこれらを正しく処理できず、派生イベントに対するサブスクライバーが基底クラスのイベントを実際に受信登録するかどうかは予測できません。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [イベント](./index.md)
- [デリゲート](../delegates/index.md)
- [アクセス修飾子](../classes-and-structs/access-modifiers.md)
- [Windows フォーム内でのイベント ハンドラーの作成](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
