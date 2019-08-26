---
title: '方法: インターフェイス メンバーを明示的に実装する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5ef8b42fe5ca07548d52b88720ea4845d2408bb1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589210"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>方法: インターフェイス メンバーを明示的に実装する (C# プログラミング ガイド)
この例では[インターフェイス](../../language-reference/keywords/interface.md)、`IDimensions`、およびクラス `Box` を宣言します。これは、インターフェイス メンバーの `getLength` と `getWidth` を明示的に実装します。 メンバーには、インターフェイス インスタンス `dimensions` を介してアクセスします。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
- `Main` メソッドでは、次の行はコメントアウトされます。これらの行でコンパイル エラーが発生するためです。 明示的に実装されるインターフェイス メンバーに、[クラス](../../language-reference/keywords/class.md) インスタンスからアクセスすることはできません。  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- `Main` メソッドの以下の行では、メソッドがインターフェイスのインスタンスから呼び出されるため、ボックスのサイズを正常に出力できます。  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [クラスと構造体](../classes-and-structs/index.md)
- "[インターフェイス](./index.md)"
- [方法: 2 つのインターフェイスのメンバーを明示的に実装する](./how-to-explicitly-implement-members-of-two-interfaces.md)
