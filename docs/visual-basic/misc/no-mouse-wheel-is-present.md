---
title: マウスのホイールが存在しません
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
ms.openlocfilehash: 0273b9838ef77c83818a8af01613a58662f37a93
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610736"
---
# <a name="no-mouse-wheel-is-present"></a>マウスのホイールが存在しません
`My.Computer.Mouse.WheelScrollLines` プロパティが呼び出されましたが、マウスにスクロール ホイールがありません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `My.Computer.Mouse.WheelExists` プロパティを呼び出す前に `My.Computer.Mouse.WheelScrollLines` プロパティを調べて、マウスにスクロール ホイールがあることを確認します。  
  
     - または -  
  
- スクロール ホイールのあるマウスをコンピュータにインストールします。  
  
## <a name="see-also"></a>関連項目

- [My.Computer.Mouse.WheelScrollLines](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)
- [My.Computer.Mouse.WheelExists](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)
- [.NET での例外の処理とスロー](../../standard/exceptions/index.md)
