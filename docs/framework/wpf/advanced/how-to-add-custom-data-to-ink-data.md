---
title: '方法: インク データにカスタム データを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: c524e30943a21426e2e5e8fe6ae009999924fead
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777053"
---
# <a name="how-to-add-custom-data-to-ink-data"></a>方法: インク データにカスタム データを追加する
カスタム データは、インクはインクがシリアル化された形式 (ISF) として保存するときに保存されるインクを追加することができます。  カスタム データを保存することができます、 <xref:System.Windows.Ink.DrawingAttributes>、 <xref:System.Windows.Ink.StrokeCollection>、または<xref:System.Windows.Ink.Stroke>します。  次の 3 つのオブジェクトに対するカスタム データを保存することを使用するデータを保存する最適な場所を決定できます。  次の 3 つのすべてのクラスは、カスタム データを格納し、アクセスのようなメソッドを使用します。  
  
 カスタム データとしては、次の種類のみを保存できます。  
  
- <xref:System.Boolean>  
  
- <xref:System.Boolean>[]  
  
- <xref:System.Byte>  
  
- <xref:System.Byte>[]  
  
- <xref:System.Char>  
  
- <xref:System.Char>[]  
  
- <xref:System.DateTime>  
  
- <xref:System.DateTime>[]  
  
- <xref:System.Decimal>  
  
- <xref:System.Decimal>[]  
  
- <xref:System.Double>  
  
- <xref:System.Double>[]  
  
- <xref:System.Int16>  
  
- <xref:System.Int16>[]  
  
- <xref:System.Int32>  
  
- <xref:System.Int32>[]  
  
- <xref:System.Int64>  
  
- <xref:System.Int64>[]  
  
- <xref:System.Single>  
  
- <xref:System.Single>[]  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <xref:System.UInt16>[]  
  
- <xref:System.UInt32>  
  
- <xref:System.UInt32>[]  
  
- <xref:System.UInt64>  
  
- <xref:System.UInt64>[]  
  
## <a name="example"></a>例  
 次の例では、追加し、カスタム データを取得する方法、<xref:System.Windows.Ink.StrokeCollection>します。  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 次の例を表示するアプリケーションの作成、<xref:System.Windows.Controls.InkCanvas>と 2 つのボタン。  ボタン、 `switchAuthor`、2 人の作成者によって使用される 2 つのペンを使用します。  ボタン`changePenColors`で各ストロークの色を変更、<xref:System.Windows.Controls.InkCanvas>作成者に従ってします。  2 つのアプリケーション定義<xref:System.Windows.Ink.DrawingAttributes>オブジェクトし、著者の描画を示す 1 つずつにカスタム プロパティを追加、<xref:System.Windows.Ink.Stroke>します。  ユーザーがクリックすると`changePenColors`アプリケーションがカスタム プロパティの値に従ってストロークの外観を変更します。  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
