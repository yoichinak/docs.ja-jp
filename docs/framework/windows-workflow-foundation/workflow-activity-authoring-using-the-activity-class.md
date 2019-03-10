---
title: アクティビティ クラスを使用したワークフロー アクティビティの作成
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: abdabc46aa54e19d5a04c5b34d6d2b9be07488d6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711864"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>アクティビティ クラスを使用したワークフロー アクティビティの作成
Windows Workflow Foundation (WF) を使用してアクティビティを作成する最も基本的な方法は、[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]から継承するクラスを作成するには<xref:System.Activities.Activity>機能を作成するまとめることでカスタム アクティビティまたはアクティビティから、[組み込みアクティビティ ライブラリ](net-framework-4-5-built-in-activity-library.md)します。 ここでは、2 つのメッセージをコンソールに書き込むアクティビティを作成する方法について説明します。

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>アクティビティ デザイナーを使ってカスタム アクティビティを作成するには

1.  Visual Studio 2012 を開きます。

2.  [ファイル]、[新規作成]、[プロジェクト] の順にクリックします。 選択**Workflow 4.0**  **Visual c#** で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。 選択**アクティビティ ライブラリ**で、**テンプレート**ウィンドウ。 新しいプロジェクトに HelloActivity という名前を付けます。

3.  新しいアクティビティを開きます。  <xref:System.Activities.Statements.Sequence> アクティビティをツールボックスからデザイナー画面にドラッグします。

4.  
  <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 入力`"Hello World"`(引用符) でに、**テキスト**フィールド。

5.  2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティを、1 つ目の下にある <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 入力`"Goodbye"`(引用符) でに、**テキスト**フィールド。
