---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 43507ac8e9b5843e8fa9496737a3d77b3a425a7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963770"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
プロパティを書き込むことができても読み取ることができないことを指定します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="rules"></a>ルール  
 **宣言コンテキスト。** `WriteOnly` は、モジュール レベルでのみ使用できます。 つまり、 `WriteOnly`プロパティの宣言コンテキストはクラス、構造体、またはモジュールである必要があり、ソースファイル、名前空間、またはプロシージャにすることはできません。  
  
 プロパティは、変数では`WriteOnly`なく、として宣言できます。  
  
## <a name="when-to-use-writeonly"></a>WriteOnly を使用する場合  
 場合によっては、コンシューマー側のコードで値を設定できても、それが何であるかを検出できないようにする必要があります。 たとえば、ソーシャル登録番号やパスワードなどの機密データは、設定されていないコンポーネントによるアクセスから保護する必要があります。 このような場合は、 `WriteOnly`プロパティを使用して値を設定できます。  
  
> [!IMPORTANT]
> `WriteOnly`プロパティを定義して使用する場合は、次の追加の保護対策を検討してください。  
  
- **オーバーライド.** プロパティがクラスのメンバーである場合は、既定の[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)にすることを許可し、 `Overridable`または`MustOverride`を宣言しません。 これにより、派生クラスがオーバーライドを通じて望ましくないアクセスを行うのを防ぐことができます。  
  
- **アクセス レベル。** プロパティの機微なデータを1つ以上の変数に保持している場合は、他のコードがアクセスできないように[プライベート](../../../visual-basic/language-reference/modifiers/private.md)変数を宣言します。  
  
- **よる.** すべての機密データをプレーンテキストではなく暗号化された形式で保存します。 悪意のあるコードが何らかの方法でメモリ領域にアクセスできた場合は、データを使用するのが難しくなります。 暗号化は、機密データをシリアル化する必要がある場合にも役立ちます。  
  
- **戻す.** プロパティを定義するクラス、構造体、またはモジュールが終了しているときに、機微なデータを既定値またはその他の意味のない値にリセットします。 これにより、メモリの領域が一般アクセス用に解放されるときに、追加の保護が提供されます。  
  
- **永続化.** 機密データを回避できる場合は、ディスクなどに保存しないでください。 また、機微なデータをクリップボードに書き込まないでください。  
  
 修飾子`WriteOnly`は、このコンテキストで使用できます。  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
