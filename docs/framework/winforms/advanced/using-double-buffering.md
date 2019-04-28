---
title: ダブル バッファリングの使用
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: ac6c9b7f2cc1fea86a75eaaf4a2dde1ea60e4f40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777157"
---
# <a name="using-double-buffering"></a>ダブル バッファリングの使用
ダブル バッファリングされたグラフィックスを使用して、複雑な描画操作が含まれているアプリケーションでちらつきを軽減することができます。 .NET Framework には、ダブル バッファリングの組み込みサポートが含まれています。 または、管理し、手動でグラフィックスをレンダリングできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ダブル バッファリングされたグラフィックス](double-buffered-graphics.md)  
 二重のバッファリングの概念や概要の .NET Framework サポートをについて説明します。  
  
 [方法: フォームとコントロールのダブル バッファリングによってグラフィックスのちらつきを軽減します。](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 既定のダブル バッファリングを .NET Framework のサポートを使用する方法を示します。  
  
 [方法: バッファリングされたグラフィックスを手動で管理します。](how-to-manually-manage-buffered-graphics.md)  
 アプリケーションでダブル バッファリングを管理する方法を示します。  
  
 [方法: バッファリングされたグラフィックスを手動で描画します。](how-to-manually-render-buffered-graphics.md)  
 ダブル バッファリングされたグラフィックスをレンダリングする方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 ダブル バッファリングをできる制御メソッド。  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 グラフィックス バッファーを作成するためのメソッドを提供します。  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 アプリケーション ドメインのバッファリングされたグラフィックス コンテキストへのアクセスを提供します。
