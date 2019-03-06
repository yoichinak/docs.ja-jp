---
title: WPF と Direct3D9 の相互運用性
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: e9d000ca2da9dd9b4c8a677e85bc9cca5b1b1b1d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372686"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF と Direct3D9 の相互運用性
Windows Presentation Foundation (WPF) アプリケーションでの Direct3D9 コンテンツを含めることができます。 このトピックでは、WPF で効率的に相互運用するための Direct3D9 コンテンツを作成する方法について説明します。  
  
> [!NOTE]
>  WPF での Direct3D9 コンテンツを使用する場合は、パフォーマンスを考慮する必要があります。 パフォーマンスを最適化する方法の詳細については、次を参照してください。 [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)します。  
  
## <a name="display-buffers"></a>バッファーを表示します。  
 <xref:System.Windows.Interop.D3DImage>クラスは、2 つ表示バッファーと呼ばれる、管理、*バック バッファー*と*フロント バッファー*します。 バック バッファーでは、Direct3D9 サーフェイスです。 バック バッファーへの変更にコピーされますフォワード フロント バッファーを呼び出すとき、<xref:System.Windows.Interop.D3DImage.Unlock%2A>メソッド。  
  
 次の図は、バック バッファーとフロント バッファー間のリレーションシップを示します。  
  
 ![D3DImage 表示バッファー](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Direct3D9 デバイスの作成  
 Direct3D9 コンテンツをレンダリングするには、Direct3D9 デバイスを作成する必要があります。 デバイスの作成に使用できる 2 つの Direct3D9 オブジェクトがない`IDirect3D9`と`IDirect3D9Ex`します。 これらのオブジェクトを使用して作成する`IDirect3DDevice9`と`IDirect3DDevice9Ex`デバイス、それぞれします。  
  
 次の方法の 1 つを呼び出すことによって、デバイスを作成します。  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista またはそれ以降のオペレーティング システムで使用して、 `Direct3DCreate9Ex` Windows 表示 Driver Model (WDDM) を使用するように構成するディスプレイを持つメソッド。 使用して、`Direct3DCreate9`他の任意のプラットフォームでのメソッド。  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Direct3DCreate9Ex メソッドの可用性  
 D3d9.dll が、`Direct3DCreate9Ex`メソッドでは、Windows Vista またはそれ以降のオペレーティング システムのみです。 Windows XP で関数を直接リンクする場合、アプリケーションは読み込みに失敗します。 確認するかどうか、`Direct3DCreate9Ex`メソッドがサポートされている、DLL を読み込む、およびプロシージャのアドレスを検索します。 次のコードをテストする方法を示しています、`Direct3DCreate9Ex`メソッド。 完全なコード例では、次を参照してください。[チュートリアル。WPF でホストするための Direct3D9 コンテンツの作成](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)です。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>HWND の作成  
 デバイスを作成するには、HWND が必要です。 一般に、使用する Direct3D9 のダミーの HWND を作成します。 次のコード例では、ダミーの HWND を作成する方法を示します。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>表示パラメーター  
 デバイスを作成する必要がありますも、`D3DPRESENT_PARAMETERS`構造体がいくつかのパラメーターのみが重要です。 これらのパラメーターを選択して、メモリ使用量を最小限に抑えます。  
  
 設定、`BackBufferHeight`と`BackBufferWidth`フィールドを 1 にします。 0 に設定すると、HWND のサイズに設定することと、します。  
  
 常に設定、`D3DCREATE_MULTITHREADED`と`D3DCREATE_FPU_PRESERVE`を防ぐためにフラグ Direct3D9 および Direct3D9 が FPU の設定を変更することを防ぐために使用するメモリの破損します。  
  
 次のコードを初期化する方法を示しています、`D3DPRESENT_PARAMETERS`構造体。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>バック バッファーのレンダー ターゲットを作成します。  
 Direct3D9 コンテンツを表示する、 <xref:System.Windows.Interop.D3DImage>、Direct3D9 サーフェスを作成して呼び出すことでそれを割り当てます、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>メソッド。  
  
### <a name="verifying-adapter-support"></a>アダプターのサポートを確認しています  
 サーフェスを作成する前に、すべてのアダプターが必要なサーフェスのプロパティをサポートすることを確認します。 アダプターが 1 つのみを表示する場合でも、WPF ウィンドウ可能性があります、システムのアダプタで表示されます。 いつでもマルチ アダプター構成を処理するための Direct3D9 コードを記述する必要があり、WPF が使用可能なアダプター間で画面を移動するので、サポートについては、すべてのアダプターを確認する必要があります。  
  
 次のコード例では、Direct3D9 用にシステム上のすべてのアダプターのサポートを確認する方法を示します。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>サーフェスを作成します。  
 サーフェスを作成する前に、デバイスの機能が対象のオペレーティング システムで良好なパフォーマンスをサポートすることを確認します。 詳細については、次を参照してください。 [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)します。  
  
 デバイスの機能を確認したら、画面を作成できます。 次のコード例では、レンダー ターゲットを作成する方法を示します。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 Windows Vista および WDDM を使用するように構成は、以降のオペレーティング システムでレンダー ターゲットのテクスチャを作成し、レベル 0 の画面に渡す、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>メソッド。 このアプローチは、ロック可能なレンダリング ターゲットのテクスチャを作成することはできませんし、パフォーマンスが低下するため、Windows xp では推奨されません。  
  
## <a name="handling-device-state"></a>デバイスの状態の処理  
 <xref:System.Windows.Interop.D3DImage>クラスは、2 つ表示バッファーと呼ばれる、管理、*バック バッファー*と*フロント バッファー*します。 バック バッファーでは、Direct3D サーフェイスです。  バック バッファーへの変更にコピーされますフォワード フロント バッファーを呼び出すとき、<xref:System.Windows.Interop.D3DImage.Unlock%2A>メソッド、ハードウェアで表示されます。 場合によっては、フロント バッファーが使用できなくなります。 画面のロック、排他 Direct3D アプリケーションを全画面表示、ユーザーの切り替え、またはその他のシステム アクティビティによって、この可用性が不足している可能性があります。 処理することによって WPF アプリケーションに通知このエラーが発生したとき、<xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>イベント。  アプリケーションが利用できなくなるフロント バッファーに応答する方法は、ソフトウェア レンダリングにフォールバックする WPF が有効になっているかどうかによって異なります。 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>メソッドは、WPF ソフトウェア レンダリングにフォールバックするかどうかを指定するパラメーターを受け取るオーバー ロードを持ちます。  
  
 呼び出すと、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29>オーバー ロードを呼び出したり、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29>オーバー ロード、`enableSoftwareFallback`パラメーターに設定`false`、フロント バッファーが使用できなくなったとは何もレンダリング システムがバック バッファーへの参照を解放表示されます。 フロント バッファーが再び使用可能、レンダリング システムが発生、 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> WPF アプリケーションに通知するイベントです。  イベント ハンドラーを作成することができます、<xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>イベントを有効な Direct3D サーフェイスを使用してレンダリングを再起動します。 レンダリングを再起動して、呼び出す必要がある<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>します。  
  
 呼び出すと、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29>オーバー ロード、`enableSoftwareFallback`パラメーターに設定`true`、レンダリング システムを呼び出す必要がないフロント バッファーが使用不能になったときにバック バッファーへの参照を保持<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>と前面バッファーが再び使用可能です。  
  
 ソフトウェア レンダリングが有効にすると、ユーザーのデバイスが使用できなくなった、レンダリング システム Direct3D サーフェイスへの参照を保持する場合があります。 Direct3D9 デバイスをご利用いただけませんかどうかを確認するには、呼び出し、`TestCooperativeLevel`メソッド。 Direct3D9Ex デバイス呼び出しを確認する、`CheckDeviceState`メソッド、ため、`TestCooperativeLevel`メソッドは非推奨し、常に成功を返します。 ユーザーのデバイスが利用できなくなると、呼び出す<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>バック バッファーへの WPF の参照を解放します。  デバイスをリセットする必要がある場合は、呼び出す<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>で、`backBuffer`パラメーターに設定`null`を呼び出して<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>でもう一度`backBuffer`Direct3D サーフェイスを有効に設定します。  
  
 呼び出す、`Reset`マルチ アダプターのサポートを実装する場合にのみ、無効なデバイスから回復する方法。 それ以外の場合、すべての Direct3D9 インターフェイスを解放し、完全に再作成します。 アダプターのレイアウトが変更された場合、変更の前に作成された Direct3D9 オブジェクトは更新されません。  
  
## <a name="handling-resizing"></a>サイズ変更の処理  
 場合、<xref:System.Windows.Interop.D3DImage>が表示されます以外のネイティブ サイズ、解像度で現在に従ってスケールが<xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>ことを除いて、<xref:System.Windows.Media.Effects.SamplingMode.Bilinear>の代わりに使用<xref:System.Windows.Media.BitmapScalingMode.Fant>します。  
  
 新規に作成する必要があります高い再現性が必要な場合場合に surface のコンテナー、<xref:System.Windows.Interop.D3DImage>サイズを変更します。  
  
 サイズ変更を処理するために、次の 3 つの可能な方法はあります。  
  
-   レイアウト システムに参加し、サイズが変更されたときに、新しい画面を作成します。 不足や、ビデオ メモリの断片化する可能性がありますので、多数のサーフェスを作成できません。  
  
-   新しい画面を作成する、固定期間、サイズ変更イベントが発生していないまで待機します。  
  
-   作成、<xref:System.Windows.Threading.DispatcherTimer>を何度も 1 秒あたりのコンテナーのディメンションを確認します。  
  
## <a name="multi-monitor-optimization"></a>マルチ モニターの最適化  
 レンダリング システムに移動するとパフォーマンスが大幅に低下する可能性を<xref:System.Windows.Interop.D3DImage>別のモニターにします。  
  
 WDDM で、モニターは、同じビデオに限り、カードを使用して`Direct3DCreate9Ex`パフォーマンスの低下はありません。 モニターが別々 のビデオ カードである場合は、パフォーマンスが低下します。 Windows xp でパフォーマンスが常に減少します。  
  
 ときに、<xref:System.Windows.Interop.D3DImage>良好なパフォーマンスの復元に対応するアダプターで新しい画面を作成する別のモニターに移動します。  
  
 パフォーマンスの低下を回避するには、マルチ モニターの具体的にはコードを記述します。 マルチ モニターのコードを記述する 1 つの方法を次に示します。  
  
1.  ポイントの検索、<xref:System.Windows.Interop.D3DImage>画面領域で、`Visual.ProjectToScreen`メソッド。  
  
2.  使用して、`MonitorFromPoint`ポイントが表示されているモニターを検索する GDI メソッド。  
  
3.  使用して、 `IDirect3D9::GetAdapterMonitor` Direct3D9 アダプターの種類のモニターを検索する方法はオンです。  
  
4.  新しいモニター新しいバック バッファーを作成し、それを割り当てるアダプターとアダプターのバック バッファーと同じでない場合、<xref:System.Windows.Interop.D3DImage>バック バッファー。  
  
> [!NOTE]
>  場合、<xref:System.Windows.Interop.D3DImage>をまたぐモニター、パフォーマンス速度が遅くなります、除く WDDM の場合と`IDirect3D9Ex`同じアダプターでします。 このような状況でパフォーマンスを向上させる方法はありません。  
  
 次のコード例では、現在のモニターを検索する方法を示します。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 モニターを更新するときに、<xref:System.Windows.Interop.D3DImage>コンテナーのサイズや位置変更、または update を使用して、モニター、 `DispatcherTimer` 1 秒あたりに数回更新します。  
  
## <a name="wpf-software-rendering"></a>WPF ソフトウェア レンダリング  
 WPF は、次の状況でのソフトウェアの UI スレッドで同期的に表示します。  
  
-   印刷  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 このような状況のいずれかが発生したとき、レンダリング システムは、<xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>ソフトウェアにハードウェアのバッファーをコピーする方法。 既定の実装、`GetRenderTargetData`サーフェスを持つメソッド。 この呼び出しは、ロック/ロック解除のパターンの外部で発生するために失敗します。 ここで、`CopyBackBuffer`メソッドを返します。`null`イメージは表示されません。  
  
 オーバーライドすることができます、<xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>メソッド、基本の実装を呼び出すと、返された場合`null`、プレース ホルダーを返すことができます<xref:System.Windows.Media.Imaging.BitmapSource>します。  
  
 基本の実装を呼び出す代わりに、独自のソフトウェア レンダリングを実装することもできます。  
  
> [!NOTE]
>  ソフトウェアでは、WPF が完全にレンダリングしている場合<xref:System.Windows.Interop.D3DImage>WPF にフロント バッファーがあるないためには表示されません。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [チュートリアル: WPF でホストするための Direct3D9 コンテンツの作成](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [チュートリアル: WPF での Direct3D9 コンテンツをホストしています。](walkthrough-hosting-direct3d9-content-in-wpf.md)
