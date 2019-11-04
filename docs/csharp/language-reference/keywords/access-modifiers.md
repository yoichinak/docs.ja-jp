---
title: アクセス修飾子 - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 7dfbc103b3fd0ebf8c349bd36dc54915782eb807
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422937"
---
# <a name="access-modifiers-c-reference"></a>アクセス修飾子 (C# リファレンス)
アクセス修飾子は、メンバーまたは型の宣言されたアクセシビリティを指定するときに使用されるキーワードです。 ここでは、4 つのアクセス修飾子について説明します。  
  
- `public`
- `protected`
- `internal`
- `private`
  
 アクセス修飾子を使用して、次の 6 つのアクセシビリティ レベルを指定できます。  
  
- [`public`](public.md):アクセスは無制限です。  
  
- [`protected`](protected.md):コンテナーであるクラスまたはそこから派生した型にアクセスが限定されます。  
  
- [`internal`](internal.md):アクセスは現在のアセンブリに限定されます。  
  
- [`protected internal`](protected-internal.md):現在のアセンブリ、または包含クラスから派生した型にアクセスが限定されます。  
  
- [`private`](private.md):コンテナーである型にアクセスが限定されます。  

- [`private protected`](private-protected.md):包含クラス、または包含クラスから派生した型にアクセスが制限されます。  
  
 このセクションでは、以下についても説明します。  
  
- [アクセシビリティ レベル](./accessibility-levels.md): 4 つのアクセス修飾子を使用して、6 つのアクセシビリティ レベルを宣言します。  
  
- [アクセシビリティ ドメイン](./accessibility-domain.md): プログラムのセクション内で、メンバーを参照できる位置を指定します。  
  
- [アクセシビリティ レベルの使用に関する制限事項](./restrictions-on-using-accessibility-levels.md): 宣言されたアクセシビリティ レベルの使用に関する制限事項をまとめたものです。  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](./index.md)
- [アクセス修飾子](../../programming-guide/classes-and-structs/access-modifiers.md)
- [アクセス キーワード](base.md)
- [修飾子](index.md)
