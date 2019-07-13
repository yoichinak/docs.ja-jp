---
title: '方法: メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 9664a3e5b5a68ae44bb129c9c550011683c81f16
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981298"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>方法: メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する (C# プログラミング ガイド)
次の例では、メソッドに[構造体](../../../csharp/language-reference/keywords/struct.md)を渡すことと[クラス](../../../csharp/language-reference/keywords/class.md) インスタンスを渡すことの違いを示します。 この例では、両方の引数 (構造体とクラス インスタンス) が値によって渡され、両方のメソッドが引数の 1 つのフィールドの値を変更します。 ただし、2 つのメソッドの結果は同じではありません。構造体を渡した場合に渡される内容と、クラスのインスタンスを渡した場合に渡される内容が異なるためです。  
  
 構造体は[値型](../../../csharp/language-reference/keywords/value-types.md)であるため、メソッドに[構造体が値によって渡される](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)と、メソッドは構造体引数のコピーを受け取って操作します。 メソッドは、呼び出し側メソッドの元の構造体にはアクセスできないため、どのような場合でもこの構造体を変更することはできません。 メソッドで変更できるのはコピーのみです。  
  
 クラス インスタンスは、値型ではなく、[参照型](../../../csharp/language-reference/keywords/reference-types.md)です。 メソッドに[参照型が値によって渡される](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)と、メソッドはクラス インスタンスへの参照のコピーを受け取ります。 つまり、メソッドは、インスタンス自体のコピーではなく、インスタンスのアドレスのコピーを受け取ることになります。 呼び出し側メソッドのクラス インスタンスにはアドレスがあり、呼び出されたメソッドのパラメータにはそのアドレスのコピーがあり、両方のアドレスが同じオブジェクトを参照します。 パラメーターにはアドレスのコピーのみが含まれるため、呼び出されたメソッドは呼び出し側メソッドのクラス インスタンスのアドレスを変更できません。 ただし、呼び出されたメソッドはアドレスを使用して、元のアドレスとコピーの両方が参照するクラス メンバーにアクセスできます。 呼び出されたメソッドがクラス メンバーを変更すると、呼び出し側メソッドの元のクラス インスタンスも変更されます。  
  
 次の例の出力はこの違いを示しています。 クラス インスタンスの `willIChange` フィールドの値はメソッド `ClassTaker` の呼び出しによって変更されます。これは、メソッドがパラメーターのアドレスを使用して、クラス インスタンスの指定されたフィールドを検索するためです。 呼び出し側メソッドの構造体の `willIChange` フィールドはメソッド `StructTaker` の呼び出しによって変更されません。これは、引数の値が、そのアドレスのコピーではなく、構造体自体のコピーであるためです。 `StructTaker` はコピーを変更し、そのコピーは、`StructTaker` の呼び出しが完了したときに失われます。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)
- [パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
