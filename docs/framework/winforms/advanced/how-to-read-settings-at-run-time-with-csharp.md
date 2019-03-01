---
title: '方法: 実行時の設定の読み取りC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974849"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>方法: C での実行時に設定の読み取り\#

アプリケーション スコープの設定とユーザー スコープの設定は、どちらも実行時に Properties オブジェクトを使用して読み取ることができます。 Properties オブジェクトは、プロジェクトのすべての既定の設定を、Properties.Settings.Default メンバーを介して公開します。  
  
## <a name="to-read-settings-at-run-time-with-c"></a>C での実行時に設定を読み取る\#
  
Properties.Settings.Default メンバーを介して適切な設定にアクセスします。 BackColor プロパティに `myColor` という名前の設定を割り当てる方法を次の例に示します。 この例を実行する前に、`myColor` という名前の `System.Drawing.Color` 型の設定を含む設定ファイルを作成しておく必要があります。 設定ファイルを作成する方法の詳細については、次を参照してください[How To:。デザイン時に新しい設定を作成](how-to-create-a-new-setting-at-design-time.md)です。  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>関連項目

- [アプリケーション設定とユーザー設定の使用](using-application-settings-and-user-settings.md)
- [方法: 実行時にユーザー設定を書き込みC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [アプリケーション設定の概要](application-settings-overview.md)
