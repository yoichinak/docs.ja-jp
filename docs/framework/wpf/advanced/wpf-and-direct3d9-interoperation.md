---
title: WPF と Direct3D9 の相互運用性
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 5fccd49b4f6fa64e5902197423d732ba0b31790e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917436"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF と Direct3D9 の相互運用性
Windows Presentation Foundation (WPF) アプリケーションに Direct3D9 コンテンツを含めることができます。 このトピックでは、WPF と効率的に相互運用できるように Direct3D9 コンテンツを作成する方法について説明します。  
  
> [!NOTE]
> WPF で Direct3D9 コンテンツを使用する場合は、パフォーマンスについても考慮する必要があります。 パフォーマンスを最適化する方法の詳細については、「 [Direct3D9 と WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)」を参照してください。  
  
## <a name="display-buffers"></a>バッファーの表示  
 クラス<xref:System.Windows.Interop.D3DImage>は、*バックバッファー*と*フロントバッファー*と呼ばれる2つの表示バッファーを管理します。 バックバッファーは Direct3D9 表面です。 バックバッファーに対する変更は、 <xref:System.Windows.Interop.D3DImage.Unlock%2A>メソッドを呼び出すときにフロントバッファーにコピーされます。  
  
 次の図は、バックバッファーとフロントバッファーの関係を示しています。  
  
 ![D3DImage の表示バッファー](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Direct3D9 デバイスの作成  
 Direct3D9 コンテンツをレンダリングするには、Direct3D9 デバイスを作成する必要があります。 デバイスの作成に使用できる Direct3D9 オブジェクトには、 `IDirect3D9`と`IDirect3D9Ex`の2つがあります。 これらのオブジェクトを使用`IDirect3DDevice9`し`IDirect3DDevice9Ex`て、デバイスとデバイスをそれぞれ作成します。  
  
 次のいずれかの方法を呼び出して、デバイスを作成します。  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista 以降のオペレーティングシステムでは、windows `Direct3DCreate9Ex` display Driver Model (WDDM) を使用するように構成された表示でメソッドを使用します。 その他`Direct3DCreate9`のプラットフォームでは、メソッドを使用します。  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Direct3DCreate9Ex メソッドの可用性  
 D3d9 には、Windows Vista `Direct3DCreate9Ex`以降のオペレーティングシステムに対してのみメソッドがあります。 Windows XP で関数を直接リンクすると、アプリケーションの読み込みに失敗します。 `Direct3DCreate9Ex`メソッドがサポートされているかどうかを判断するには、DLL を読み込み、proc アドレスを探します。 次のコードは、 `Direct3DCreate9Ex`メソッドをテストする方法を示しています。 完全なコード例について[は、「チュートリアル:WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)でホストするための Direct3D9 コンテンツの作成。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>HWND の作成  
 デバイスを作成するには HWND が必要です。 一般に、Direct3D9 が使用するダミーの HWND を作成します。 次のコード例は、ダミーの HWND を作成する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>パラメーターを表示する  
 デバイスを作成するには`D3DPRESENT_PARAMETERS`構造体も必要ですが、いくつかのパラメーターのみが重要です。 メモリフットプリントを最小限に抑えるために、これらのパラメーターが選択されています。  
  
 `BackBufferHeight`フィールドと`BackBufferWidth`フィールドを1に設定します。 これらを0に設定すると、HWND の大きさに設定されます。  
  
 Direct3D9 によっ`D3DCREATE_MULTITHREADED`て`D3DCREATE_FPU_PRESERVE`使用されるメモリが破損しないようにし、Direct3D9 が FPU 設定を変更しないようにするには、フラグとフラグを常に設定します。  
  
 次のコードは、 `D3DPRESENT_PARAMETERS`構造体を初期化する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>バックバッファーレンダーターゲットを作成しています  
 で<xref:System.Windows.Interop.D3DImage>Direct3D9 コンテンツを表示するには、Direct3D9 サーフェイスを作成し、 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>メソッドを呼び出して割り当てます。  
  
### <a name="verifying-adapter-support"></a>アダプターサポートの検証  
 サーフェイスを作成する前に、すべてのアダプターが必要なサーフェイスプロパティをサポートしていることを確認します。 表示するアダプターが1つだけの場合でも、WPF ウィンドウはシステム内のすべてのアダプターに表示されることがあります。 マルチアダプター構成を処理する Direct3D9 コードを作成する必要があります。また、WPF が使用可能なアダプター間でサーフェイスを移動する可能性があるため、すべてのアダプターがサポートされているかどうかを確認する必要があります。  
  
 次のコード例は、システム上のすべてのアダプターの Direct3D9 サポートを確認する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>サーフェイスの作成  
 Surface を作成する前に、デバイスの機能がターゲットのオペレーティングシステムで良好なパフォーマンスをサポートしていることを確認します。 詳細については、「 [Direct3D9 と WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)」を参照してください。  
  
 デバイスの機能を確認したら、surface を作成できます。 レンダーターゲットを作成する方法を次のコード例に示します。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 WDDM を使用するように構成されている Windows Vista 以降のオペレーティングシステムでは、レンダーターゲットテクスチャを作成し、 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>メソッドにレベル0のサーフェイスを渡すことができます。 この方法は Windows XP では推奨されません。ロック可能なレンダーターゲットテクスチャを作成することはできず、パフォーマンスが低下するためです。  
  
## <a name="handling-device-state"></a>デバイスの状態の処理  
 クラス<xref:System.Windows.Interop.D3DImage>は、*バックバッファー*と*フロントバッファー*と呼ばれる2つの表示バッファーを管理します。 バックバッファーは、Direct3D サーフェイスです。  バックバッファーに対する変更は、 <xref:System.Windows.Interop.D3DImage.Unlock%2A>メソッドを呼び出したときにフロントバッファーにコピーされ、ハードウェア上に表示されます。 場合によっては、フロントバッファーが使用できなくなることがあります。 この可用性の欠如は、画面のロック、全画面の専用 Direct3D アプリケーション、ユーザー切り替え、またはその他のシステムアクティビティによって発生する可能性があります。 このエラーが発生すると、 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>イベントを処理することによって、WPF アプリケーションに通知されます。  アプリケーションがフロントバッファーを使用できなくなった場合の応答は、WPF がソフトウェアレンダリングにフォールバックすることが有効になっているかどうかによって異なります。 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>メソッドには、WPF がソフトウェアレンダリングにフォールバックするかどうかを指定するパラメーターを受け取るオーバーロードがあります。  
  
 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29>オーバーロードを呼び出すか、パラメーターを<xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29>に`false`設定し`enableSoftwareFallback`てオーバーロードを呼び出すと、フロントバッファーが使用できなくなったときに、レンダリングシステムによってバックバッファーへの参照が解放されます。さ. フロントバッファーが再び使用可能になると、レンダリングシステムに<xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>よってイベントが発生し、WPF アプリケーションに通知されます。  <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>イベントのイベントハンドラーを作成して、有効な Direct3D サーフェイスで再び描画を再開することができます。 レンダリングを再開するには、 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>を呼び出す必要があります。  
  
 パラメーター <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29>をに`enableSoftwareFallback` <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>設定してオーバーロードを呼び出すと、フロントバッファーが使用できなくなったときに、レンダリングシステムによってバックバッファーへの参照が保持されるため、前面にあるときにを呼び出す必要はありません。 `true`バッファーを再度使用できます。  
  
 ソフトウェアレンダリングが有効になっている場合、ユーザーのデバイスが使用できなくなっても、レンダリングシステムが Direct3D サーフェイスへの参照を保持している場合があります。 Direct3D9 デバイスが使用できないかどうかを確認`TestCooperativeLevel`するには、メソッドを呼び出します。 Direct3D9Ex デバイスを確認するには`CheckDeviceState` 、メソッドが非`TestCooperativeLevel`推奨とされ、常に success が返されるため、メソッドを呼び出します。 ユーザーデバイスが使用できなくなった場合<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>は、を呼び出して、バックバッファーへの WPF の参照を解放します。  デバイスをリセットする必要がある場合は<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 、 `backBuffer`パラメーターをに`null`設定してを呼び出し、を`backBuffer`有効な Direct3D サーフェイスに設定してを再度呼び出し<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>ます。  
  
 複数アダプター `Reset`のサポートを実装している場合にのみ、メソッドを呼び出して、無効なデバイスから回復します。 それ以外の場合は、すべての Direct3D9 インターフェイスを解放し、それらを完全に再作成します。 アダプターのレイアウトが変更された場合、変更前に作成された Direct3D9 オブジェクトは更新されません。  
  
## <a name="handling-resizing"></a>サイズ変更の処理  
 がネイティブサイズ以外の解像度で表示される場合、がに<xref:System.Windows.Media.BitmapScalingMode.Fant>置き換えられる<xref:System.Windows.Media.Effects.SamplingMode.Bilinear>点を除い<xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>て、は現在のに従ってスケーリングされます。 <xref:System.Windows.Interop.D3DImage>  
  
 より忠実度が高い場合は、の<xref:System.Windows.Interop.D3DImage>コンテナーのサイズが変更されたときに新しいサーフェイスを作成する必要があります。  
  
 サイズ変更を処理するには、3つの方法があります。  
  
- レイアウトシステムに参加し、サイズが変化したときに新しいサーフェイスを作成します。 ビデオメモリを消費したり、フラグメント化したりする可能性があるため、あまり多くのサーフェイスを作成しないでください。  
  
- 新しいサーフェイスを作成するために一定期間、サイズ変更イベントが発生するまで待機します。  
  
- コンテナーの<xref:System.Windows.Threading.DispatcherTimer>ディメンションを1秒間に何度か確認するを作成します。  
  
## <a name="multi-monitor-optimization"></a>マルチモニターの最適化  
 レンダリングシステムがを別のモニターに移動すると<xref:System.Windows.Interop.D3DImage> 、パフォーマンスが大幅に低下する可能性があります。  
  
 WDDM では、モニターが同じビデオカード上にあり、を使用する限り`Direct3DCreate9Ex`、パフォーマンスが低下することはありません。 モニターが別のビデオカードにある場合は、パフォーマンスが低下します。 Windows XP では、パフォーマンスは常に低下します。  
  
 を別のモニターに移動すると、対応するアダプターに新しい画面を作成して、良好なパフォーマンスを復元できます。<xref:System.Windows.Interop.D3DImage>  
  
 パフォーマンスの低下を回避するには、マルチモニターケース専用のコードを記述します。 次の一覧は、マルチモニターコードを記述する1つの方法を示しています。  
  
1. メソッド`Visual.ProjectToScreen`を使用して<xref:System.Windows.Interop.D3DImage> 、画面領域内のポイントを検索します。  
  
2. `MonitorFromPoint` GDI メソッドを使用して、ポイントを表示しているモニターを見つけます。  
  
3. このモニター `IDirect3D9::GetAdapterMonitor`がある Direct3D9 アダプターを検索するには、メソッドを使用します。  
  
4. アダプターがバックバッファーを使用するアダプターと同じでない場合は、新しいモニターに新しいバックバッファーを作成し、 <xref:System.Windows.Interop.D3DImage>バックバッファーに割り当てます。  
  
> [!NOTE]
> またがっが<xref:System.Windows.Interop.D3DImage>監視している場合、WDDM と`IDirect3D9Ex`同じアダプタにある場合を除き、パフォーマンスは低下します。 このような状況では、パフォーマンスを向上させる方法はありません。  
  
 次のコード例は、現在のモニターを検索する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 コンテナーのサイズまたは<xref:System.Windows.Interop.D3DImage>位置が変更されたときにモニターを更新するか、 `DispatcherTimer` 1 秒間に数回更新されるを使用してモニターを更新します。  
  
## <a name="wpf-software-rendering"></a>WPF のソフトウェアレンダリング  
 WPF は、次のような場合に、ソフトウェアの UI スレッド上で同期的にレンダリングされます。  
  
- 印刷  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 これらの状況のいずれかが発生すると、レンダリング<xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>システムはメソッドを呼び出して、ハードウェアバッファーをソフトウェアにコピーします。 既定の実装では`GetRenderTargetData` 、画面を使用してメソッドを呼び出します。 この呼び出しはロック/ロック解除パターンの外側で行われるため、失敗する可能性があります。 この場合、メソッドは`CopyBackBuffer`を返し`null` 、イメージは表示されません。  
  
 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>メソッドをオーバーライドし、基本実装を呼び出すことができます。 `null`を返した場合は、 <xref:System.Windows.Media.Imaging.BitmapSource>プレースホルダーを返すことができます。  
  
 基本実装を呼び出す代わりに、独自のソフトウェアレンダリングを実装することもできます。  
  
> [!NOTE]
> Wpf が完全にソフトウェアでレンダリングさ<xref:System.Windows.Interop.D3DImage>れている場合、wpf にはフロントバッファーがないため、は表示されません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [チュートリアル: WPF でホストするための Direct3D9 コンテンツの作成](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [チュートリアル: WPF での Direct3D9 コンテンツのホスト](walkthrough-hosting-direct3d9-content-in-wpf.md)
