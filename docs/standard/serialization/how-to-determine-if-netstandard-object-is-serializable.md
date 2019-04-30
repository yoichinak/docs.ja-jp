---
title: .NET Standard のオブジェクトがシリアル化可能なかどうかを判断する方法
description: 実行時に .NET Standard の型をシリアル化できるかどうかを確認する方法を示します。
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018760"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>.NET Standard のオブジェクトがシリアル化可能なかどうかを判断する方法

.NET Standard は、型とそのバージョンの標準に準拠している特定の .NET 実装に存在する必要があるメンバーを定義する仕様です。 ただし、.NET Standard 定義しません、型をシリアル化するかどうか。 .NET 標準ライブラリで定義された型がでマークされていない、<xref:System.SerializableAttribute>属性。 代わりに、.NET Framework、.NET Core などの特定の .NET 実装が自由に、特定の型がシリアル化できるかどうかを決定します。 

対象とする .NET Standard のライブラリを開発した場合は、.NET Standard をサポートする任意の .NET 実装によって、ライブラリを使用できます。 つまり、ことはできませんがわかっている事前に特定の型がシリアル化できるかどうかのみ、実行時にシリアル化可能なことがあるかどうかを確認できます。

値を取得することによって、オブジェクトが実行時にシリアル化可能かどうかを判断できます、<xref:System.Type.IsSerializable>のプロパティを<xref:System.Type>そのオブジェクトの型を表すオブジェクト。 次の例では、1 つの実装を提供します。 定義、`IsSerializable(Object)`拡張メソッドを示すかどうか、<xref:System.Object>インスタンスをシリアル化することができます。

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

任意のオブジェクトにするかどうかをシリアル化でき、次の例として、現在の .NET 実装に逆シリアル化を判断するメソッドを渡します。

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>関連項目

- [バイナリ シリアル化](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
