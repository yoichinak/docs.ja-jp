---
title: '方法: 設計時に新しい設定を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037902"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>方法: デザイン時に新しい設定を作成する

Visual Studio の設定デザイナーを使用して、デザイン時に新しい設定を作成できます。 設定デザイナーは、新しい設定を作成し、それらの設定のプロパティを指定できるグリッド形式のインターフェイスです。 新しい設定の名前、値、種類、およびスコープを指定する必要があります。 設定が作成されると、コードでアクセスできるようになります。

## <a name="create-a-new-setting-at-design-time-in-c"></a>C でデザイン時に新しい設定を作成する\#

1. Visual Studio を開きます。

2. **ソリューションエクスプローラー**で、プロジェクトの **[プロパティ]** ノードを展開します。

3. 新しい設定を追加する設定ファイルをダブルクリックします。 このファイルの既定の名前は設定です。設定です。

4. 設定デザイナーで、設定の **[名前]** 、 **[値]** 、 **[種類]** 、 **[スコープ]** を設定します。 各行は1つの設定を表します。

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a>デザイン時に Visual Basic で新しい設定を作成する

1. Visual Studio を開きます。

2. **ソリューションエクスプローラー**で、プロジェクトノードを右クリックし、 **[プロパティ]** を選択します。

3. **[プロパティ]** ページで、 **[設定]** タブを選択します。

4. 設定デザイナーで、設定の **[名前]** 、 **[値]** 、 **[種類]** 、 **[スコープ]** を設定します。 各行は1つの設定を表します。

## <a name="see-also"></a>関連項目

- [アプリケーション設定とユーザー設定の使用](using-application-settings-and-user-settings.md)
- [アプリケーション設定の概要](application-settings-overview.md)
- [方法: デザイン時に既存の設定の値を変更する](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
