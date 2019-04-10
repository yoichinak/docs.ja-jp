---
title: '方法: 設計時に新しい設定を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 03a96298af68579bb2e67299688928dee0f517de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198583"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>方法: 設計時に新しい設定を作成する
設定デザイナーを使用して、デザイン時に新しい設定を作成できます。 設定デザイナーは、新しい設定を作成し、これらの設定のプロパティを指定できるようにするグリッド スタイルのインターフェイスです。 名前、値、型、および、新しい設定のスコープを指定する必要があります。 設定が作成されると、コードでアクセス可能な。  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a>C でのデザイン時に新しい設定を作成するには\#
  
1.  **ソリューション エクスプ ローラー**、展開、**プロパティ**プロジェクトのノード。  
  
2.  新しい設定を追加する .settings ファイルをダブルクリックします。 このファイルの既定の名前は Settings.settings ですです。  
  
3.  設定デザイナーで、名前、値、型、および設定のスコープを設定します。 各行は、1 つの設定を表します。  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a>Visual Basic でのデザイン時に新しい設定を作成するには  
  
1.  **ソリューション エクスプ ローラー**をプロジェクト ノードを右クリックして**プロパティ**します。  
  
2.  **プロパティ**] ページで、[、**設定**タブ。  
  
3.  設定デザイナーで、名前、値、型、および設定のスコープを設定します。 各行は、1 つの設定を表します。  
  
## <a name="see-also"></a>関連項目

- [アプリケーション設定とユーザー設定の使用](using-application-settings-and-user-settings.md)
- [アプリケーション設定の概要](application-settings-overview.md)
- [方法: 設計時に既存の設定の値を変更する](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
