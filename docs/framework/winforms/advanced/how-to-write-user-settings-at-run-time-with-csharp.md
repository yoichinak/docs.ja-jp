---
title: '方法: 実行時にユーザー設定を書き込みC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981596"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>方法: C での実行時にユーザー設定を書き込み\#

アプリケーション スコープの設定は読み取り専用であり、デザイン時、またはアプリケーション セッション間に .config ファイルを変更することによってのみ変更できます。 ただし、ユーザー スコープの設定は、プロパティ値を変更する場合と同様に、実行時に書き込むことができます。 新しい値は、アプリケーションのセッションの実行中に永続化します。 Save メソッドを呼び出すことによって、アプリケーション セッション間で、設定の変更を永続化することができます。  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>方法: 書き込みし、C での実行時にユーザー設定を永続化\#
  
1. この設定にアクセスし、この例で示すように、新しい値を割り当てます。  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. アプリケーション セッション間で、設定の変更を永続化する場合は、この例で示すように Save メソッドを呼び出します。  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
ユーザー設定は、ユーザーの非表示のローカル アプリケーション データ フォルダーのサブフォルダー内のファイルに保存されます。  
  
## <a name="see-also"></a>関連項目

- [アプリケーション設定とユーザー設定の使用](using-application-settings-and-user-settings.md)
- [方法: 実行時の設定の読み取りC#](how-to-read-settings-at-run-time-with-csharp.md)
- [アプリケーション設定の概要](application-settings-overview.md)
