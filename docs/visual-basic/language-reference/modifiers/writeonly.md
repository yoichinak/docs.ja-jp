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
ms.openlocfilehash: 163ec17f3ea96744290c54a73054ab132f842127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647668"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
プロパティの記述が読み取らないことを指定します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="rules"></a>ルール  
 **宣言コンテキスト。** `WriteOnly` は、モジュール レベルでのみ使用できます。 これは、意味の宣言のコンテキストを`WriteOnly`プロパティは、クラス、構造体、またはモジュールにある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。  
  
 としてプロパティを宣言する`WriteOnly`が変数ではありません。  
  
## <a name="when-to-use-writeonly"></a>WriteOnly を使用する場合  
 値の設定ができないことができる、使用側コードたい場合があります。 たとえば、ソーシャル登録番号やパスワードなどの機密データを設定していない任意のコンポーネントによるアクセスから保護する必要があります。 このような場合は、使用することができます、`WriteOnly`プロパティ値を設定します。  
  
> [!IMPORTANT]
>  定義して使用するときに、`WriteOnly`プロパティ、次の追加の保護対策を検討してください。  
  
- **オーバーライドします。** プロパティがクラスのメンバーである場合は、許可する既定の[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)を宣言していないと`Overridable`または`MustOverride`します。 これは派生クラスが上書きすることによって、不要なアクセスを作成することを防ぎます。  
  
- **アクセス レベルです。** 1 つまたは複数の変数で、プロパティの機密データを保持する場合では、宣言[プライベート](../../../visual-basic/language-reference/modifiers/private.md)できるように、その他のコードはアクセスできません。  
  
- **暗号化。** プレーン テキストではなく、暗号化された形式では、すべての機密データを格納します。 何らかの方法で、悪意のあるコードのメモリの領域にアクセスできる場合より少なく、データを使用します。 暗号化も機密データをシリアル化する必要がある場合に役立ちます。  
  
- **リセットしています。** クラス、構造体、またはプロパティを定義するモジュールが終了するときに既定値または他の意味のない値に機微なデータをリセットします。 これにより、一般的なアクセスにそのメモリ領域が解放されるとき、保護を強化できます。  
  
- **永続化します。** 回避する場合、ディスクなどに、機密データは保持されません。 クリップボードには、機密データは書き込みませんも。  
  
 `WriteOnly`修飾子は、このコンテキストで使用できます。  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
