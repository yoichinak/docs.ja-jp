---
title: 'チュートリアル: WPF でホストするための Direct3D9 コンテンツの作成'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 8acef4a52c9317618485a7c46c1e22cc2524dd69
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379602"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>チュートリアル: WPF でホストするための Direct3D9 コンテンツの作成
このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションでホストするための適切な Direct3D9 コンテンツを作成する方法を示します。 WPF アプリケーションでの Direct3D9 コンテンツのホストの詳細については、[WPF と Direct3D9 の相互運用性](wpf-and-direct3d9-interoperation.md)を参照してください。

 このチュートリアルでは次のタスクを実行します。

-   Direct3D9 プロジェクトを作成します。

-   WPF アプリケーションでホストするための Direct3D9 プロジェクトを構成します。

 完了したら、WPF アプリケーションで使用するための Direct3D9 コンテンツを含む DLL 必要があります。

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを実行するには、次のコンポーネントが必要です。

-   Visual Studio 2010。

-   DirectX 9 以降の SDK です。

## <a name="creating-the-direct3d9-project"></a>Direct3D9 プロジェクトを作成します。
 最初の手順では、作成および Direct3D9 プロジェクトを構成します。

#### <a name="to-create-the-direct3d9-project"></a>Direct3D9 プロジェクトを作成するには

1.  C++ という名前で新しい Win32 プロジェクトを作成`D3DContent`です。

     Win32 アプリケーション ウィザードが開き、ようこそ画面が表示されます。

2.  **[次へ]** をクリックします。

     [アプリケーション設定] 画面が表示されます。

3.  **アプリケーションの種類:** セクションで、 **DLL**オプション。

4.  **[完了]** をクリックします。

     D3DContent プロジェクトが生成されます。

5.  ソリューション エクスプ ローラーでは、D3DContent プロジェクトを右クリックして**プロパティ**します。

     **D3DContent プロパティ ページ** ダイアログ ボックスが表示されます。

6.  選択、 **C/C++** ノード。

7.  **追加のインクルード ディレクトリ**フィールドに、DirectX の場所は、フォルダーを指定します。 このフォルダーの既定の場所は %ProgramFiles%\Microsoft DirectX SDK (*バージョン*) \Include します。

8.  ダブルクリックして、**リンカー**ノードを展開します。

9. **追加のライブラリ ディレクトリ**フィールドに、DirectX のライブラリ フォルダーの場所を指定します。 このフォルダーの既定の場所は %ProgramFiles%\Microsoft DirectX SDK (*バージョン*) \Lib\x86 します。

10. 選択、**入力**ノード。

11. **追加の依存関係**フィールドに、追加、`d3d9.lib`と`d3dx9.lib`ファイル。

12. ソリューション エクスプ ローラーの追加という名前の新しいモジュール定義ファイル (.def)`D3DContent.def`をプロジェクトにします。

## <a name="creating-the-direct3d9-content"></a>Direct3D9 コンテンツを作成します。
 最適なパフォーマンスを得るには、Direct3D9 コンテンツは特定の設定を使用する必要があります。 次のコードでは、最適なパフォーマンス特性を持つ Direct3D9 サーフェスを作成する方法を示します。 詳細については、[Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)を参照してください。

#### <a name="to-create-the-direct3d9-content"></a>Direct3D9 コンテンツを作成するには

1.  ソリューション エクスプ ローラーを使用して、次の名前のプロジェクトに 3 つの C++ クラスを追加します。

     `CRenderer` (で仮想デストラクター)

     `CRendererManager`

     `CTriangleRenderer`

2.  Renderer.h をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3.  Renderer.cpp をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4.  RendererManager.h をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5.  RendererManager.cpp をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6.  TriangleRenderer.h をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7.  TriangleRenderer.cpp をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8.  Stdafx.h をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Dllmain.cpp をコード エディターで開くし、自動的に生成されたコードを次のコードに置き換えます。

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. D3DContent.def をコード エディターで開きます。

11. 自動的に生成されたコードを次のコードに置き換えます。

    ```
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. プロジェクトをビルドします。

## <a name="next-steps"></a>次の手順

-   WPF アプリケーションでの Direct3D9 コンテンツをホストします。 詳細については、「[チュートリアル:WPF での Direct3D9 コンテンツをホストしている](walkthrough-hosting-direct3d9-content-in-wpf.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [チュートリアル: WPF での Direct3D9 コンテンツをホストしています。](walkthrough-hosting-direct3d9-content-in-wpf.md)
