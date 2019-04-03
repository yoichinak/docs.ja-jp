---
title: オブジェクトまたはクラスがこのイベント セットをサポートしていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: 2e00bdd624b54e19f19b6dabf6681bbf89709e60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822584"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>オブジェクトまたはクラスがこのイベント セットをサポートしていません。
使用して、`WithEvents`変数でコンポーネントを指定した一連のイベントのイベント ソースとして使用できません。 オブジェクトのイベントをシンク、別のオブジェクトを作成したいなど`Implements`最初のオブジェクト。 実装されたオブジェクトからイベントをシンクする想像がこれとは限りません場合です。 `Implements` メソッドとプロパティのインターフェイスを実装するだけです。 `WithEvents` プライベートはサポートされていません`UserControls`させる型情報が必要なため、`ObjectEvent`実行時に使用できません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  ソース イベントではないコンポーネントのイベントをシンクすることはできません。  
  
## <a name="see-also"></a>関連項目

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)
