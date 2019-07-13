---
title: グラフィックス コンテナーの使用
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766156"
---
# <a name="using-graphics-containers"></a>グラフィックス コンテナーの使用
A<xref:System.Drawing.Graphics>オブジェクトなどのメソッドを提供<xref:System.Drawing.Graphics.DrawLine%2A>、 <xref:System.Drawing.Graphics.DrawImage%2A>、および<xref:System.Drawing.Graphics.DrawString%2A>ベクター イメージ、ラスター イメージ、およびテキストを表示するためです。 A<xref:System.Drawing.Graphics>オブジェクトにも、品質とは、描画される項目の向きに影響を与えるいくつかのプロパティがあります。 たとえば、スムージング モード プロパティは、線と曲線にアンチエイリアシングを適用し、位置と回転は、描画される項目のワールド変換プロパティに影響を与えますかどうかを決定します。  
  
 A<xref:System.Drawing.Graphics>オブジェクトが特定のディスプレイ デバイスに関連付けられています。 使用すると、<xref:System.Drawing.Graphics>ウィンドウで、描画するオブジェクト、<xref:System.Drawing.Graphics>オブジェクトは、その特定のウィンドウに関連付けられてもします。  
  
 A<xref:System.Drawing.Graphics>オブジェクトはコンテナーとして描画に影響を与えるプロパティのセットを保持していると、デバイスに固有の情報にリンクされます。 内で、既存のセカンダリのコンテナーを作成する<xref:System.Drawing.Graphics>オブジェクトを呼び出すことによって、<xref:System.Drawing.Graphics.BeginContainer%2A>メソッドの<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Graphics オブジェクトの状態の管理](managing-the-state-of-a-graphics-object.md)  
 について説明します、品質の設定、クリッピング領域との変換を管理する方法、<xref:System.Drawing.Graphics>オブジェクト。  
  
 [入れ子になっているグラフィックス コンテナーの使用](using-nested-graphics-containers.md)  
 コンテナーを使用しての状態を制御する方法を示しています、<xref:System.Drawing.Graphics>オブジェクト。
