---
title: 'チュートリアル: WPF での Direct3D9 コンテンツのホスト'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 2c31c044aa50a74255a61da1675037ab3d09f615
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053448"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>チュートリアル: WPF での Direct3D9 コンテンツのホスト

このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションで Direct3D9 コンテンツをホストする方法について説明します。

このチュートリアルでは次のタスクを実行します。

- Direct3D9 コンテンツをホストする WPF プロジェクトを作成します。

- Direct3D9 コンテンツをインポートします。

- <xref:System.Windows.Interop.D3DImage>クラスを使用して Direct3D9 の内容を表示します。

 完了すると、WPF アプリケーションで Direct3D9 コンテンツをホストする方法がわかります。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- Visual Studio

- DirectX SDK 9 以降。

- WPF 互換形式の Direct3D9 コンテンツを含む DLL。 詳細については、「 [WPF と Direct3D9 の相互運用](wpf-and-direct3d9-interoperation.md)と[チュートリアル:WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)でホストするための Direct3D9 コンテンツの作成。

## <a name="creating-the-wpf-project"></a>WPF プロジェクトの作成

最初の手順では、WPF アプリケーション用のプロジェクトを作成します。

### <a name="to-create-the-wpf-project"></a>WPF プロジェクトを作成するには

という名前C# `D3DHost`のビジュアルで新しい WPF アプリケーションプロジェクトを作成します。 詳細については、「[チュートリアル:初めての WPF デスクトップ](../getting-started/walkthrough-my-first-wpf-desktop-application.md)アプリケーション。

Mainwindow.xaml がに[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]表示されます。

## <a name="importing-the-direct3d9-content"></a>Direct3D9 コンテンツのインポート

`DllImport`属性を使用して、アンマネージ DLL から Direct3D9 コンテンツをインポートします。

### <a name="to-import-direct3d9-content"></a>Direct3D9 コンテンツをインポートするには

1. コードエディターで MainWindow.xaml.cs を開きます。

2. 自動的に生成されたコードを次のコードに置き換えます。

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a>Direct3D9 コンテンツのホスト

最後に、 <xref:System.Windows.Interop.D3DImage>クラスを使用して、Direct3D9 コンテンツをホストします。

### <a name="to-host-the-direct3d9-content"></a>Direct3D9 コンテンツをホストするには

1. Mainwindow.xaml で、自動的に生成された XAML を次の XAML に置き換えます。

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. プロジェクトをビルドします。

3. Direct3D9 コンテンツを含む DLL を bin/Debug フォルダーにコピーします。

4. F5 キーを押してプロジェクトを実行します。

    Direct3D9 コンテンツが WPF アプリケーション内に表示されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
