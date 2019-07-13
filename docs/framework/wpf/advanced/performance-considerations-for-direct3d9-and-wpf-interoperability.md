---
title: Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 1371fa901bebc503a0091f3229a8fd7e6ccc2c86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772854"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項
Direct3D9 コンテンツをホストするにを使用して、<xref:System.Windows.Interop.D3DImage>クラス。 Direct3D9 コンテンツをホストするいると、アプリケーションのパフォーマンスに影響を与えることができます。 このトピックでは、Windows Presentation Foundation (WPF) アプリケーションでの Direct3D9 コンテンツをホストする場合は、パフォーマンスを最適化するベスト プラクティスについて説明します。 これらのベスト プラクティスを使用する方法は、<xref:System.Windows.Interop.D3DImage>とベスト プラクティスを Windows Vista、Windows XP を使用するいるし、マルチ モニターを表示します。  
  
> [!NOTE]
>  これらのベスト プラクティスを示すコード例では、次を参照してください。 [WPF と Direct3D9 の相互運用性](wpf-and-direct3d9-interoperation.md)します。  
  
## <a name="use-d3dimage-sparingly"></a>D3DImage を多用しません。  
 Direct3D9 コンテンツがホストされている、<xref:System.Windows.Interop.D3DImage>インスタンスが純粋な Direct3D アプリケーションのように高速としてレンダリングされません。 サーフェイスのコピーとコマンド バッファーをフラッシュするには、コストのかかる操作を指定できます。 数値として<xref:System.Windows.Interop.D3DImage>インスタンスが増えると、詳細のフラッシュが発生して、パフォーマンスが低下します。 したがって、使用する必要があります<xref:System.Windows.Interop.D3DImage>限定的に使用します。  
  
## <a name="best-practices-on-windows-vista"></a>Windows Vista でのベスト プラクティス  
 Windows 表示 Driver Model (WDDM) を使用するように構成されたディスプレイを使用した Windows Vista の最適なパフォーマンス上、Direct3D9 サーフェスを作成、`IDirect3DDevice9Ex`デバイス。 これにより、サーフェイスを共有できます。 ビデオ カードをサポートする必要があります、`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`と`D3DCAPS2_CANSHARERESOURCE`Windows Vista のドライバーの機能です。 その他の設定では、パフォーマンスが大幅に低下するためのソフトウェアをコピーする画面が発生します。  
  
> [!NOTE]
>  Windows Vista、Windows XP 表示 Driver Model (XDDM) を使用するように構成する、表示にされている場合、画面が設定に関係なく、ソフトウェアを常にコピーします。 サーフェイスのコピーがハードウェアで実行されるため、WDDM を使用する場合の適切な設定とビデオ カードでは、パフォーマンスを向上させる Windows Vista 上に表示されます。  
  
## <a name="best-practices-on-windows-xp"></a>Windows XP のベスト プラクティス  
 Windows XP Display Driver Model (XDDM) を使用して Windows XP で最適なパフォーマンスが正しく動作する lockable サーフェスを作成時に、`IDirect3DSurface9::GetDC`メソッドが呼び出されます。 内部的には、`BitBlt`メソッドは、ハードウェア デバイス間で、画面を転送します。 `GetDC`メソッドは常に XRGB サーフェスで機能します。 ただし、SP3 または SP2、Windows XP を実行しているクライアント コンピューターと、クライアントは階層化ウィンドウの機能の修正プログラムもある場合は、このメソッドはのみ ARGB サーフェスで機能します。 ビデオ カードをサポートする必要があります、`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`ドライバー機能。  
  
 デスクトップの表示を 16 ビットの深さは、パフォーマンスを大幅に短縮できます。 32 ビット デスクトップをお勧めします。  
  
 Windows Vista および Windows XP を開発している場合は、Windows XP でパフォーマンスをテストします。 問題では Windows XP でのビデオ メモリ不足です。 さらに、 <xref:System.Windows.Interop.D3DImage> Windows XP で複数のビデオ メモリと必要な余分なビデオ メモリ コピーにより、Windows Vista WDDM よりも帯域幅を使用します。 そのため、パフォーマンスがさらに悪いことよりも Windows Vista での Windows XP のビデオ ハードウェアが同じであることができます。  
  
> [!NOTE]
>  XDDM は Windows XP と Windows Vista; の両方で使用できます。ただし、WDDM は Windows Vista でのみ使用できます。  
  
## <a name="general-best-practices"></a>一般的なベスト プラクティス  
 デバイスを作成するときに使用して、`D3DCREATE_MULTITHREADED`作成フラグ。 パフォーマンスを低下するためこれが、WPF レンダリング システムは、別のスレッドからこのデバイスでメソッドを呼び出します。 2 つのスレッドが同時に、デバイスをアクセスできるように、正しく、ロックのプロトコルに従うことを確認します。  
  
 レンダリングが管理されている WPF のスレッドで実行される場合を使用してデバイスを作成することが強く推奨される、`D3DCREATE_FPU_PRESERVE`作成フラグ。 この設定がない、D3D 表示モードの WPF の倍精度演算の精度が低下し、レンダリングの問題が発生することができます。  
  
 並べて表示、<xref:System.Windows.Interop.D3DImage>を並べて表示する場合か、ハードウェアをサポートしていない非 pow2 サーフェスを並べて表示しない限り、高速では、<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>を格納している、<xref:System.Windows.Interop.D3DImage>します。  
  
## <a name="best-practices-for-multi-monitor-displays"></a>マルチ モニター表示のためのベスト プラクティス  
 複数のモニターがあるコンピューターを使用している場合は、前述のベスト プラクティスに従う必要があります。 マルチ モニターの構成のいくつか追加のパフォーマンスの考慮事項もあります。  
  
 バック バッファーを作成するときに、特定のデバイスと、アダプター上に作成されますが、WPF はアダプタでフロント バッファーを表示することがあります。 フロント バッファーを更新するアダプター間でコピーと、非常に高価なことができます。 複数のビデオ カードとは、WDDM を使用するように構成された Windows Vista で、`IDirect3DDevice9Ex`デバイス フロント バッファーが別のアダプターでも同じビデオ カードにある場合は、パフォーマンスの低下はありません。 ただし、Windows XP と複数のビデオ カードで XDDM では、大幅なパフォーマンスの低下フロント バッファーが表示されたら、バック バッファーとは異なるアダプター。 詳細については、次を参照してください。 [WPF と Direct3D9 の相互運用性](wpf-and-direct3d9-interoperation.md)します。  
  
## <a name="performance-summary"></a>パフォーマンスの概要  
 次の表では、オペレーティング システム、ピクセル形式、およびサーフェイスのロック可能性の関数としてフロント バッファーの更新プログラムのパフォーマンスを表示します。 フロント バッファーとバック バッファーは、同じアダプター上にあると見なされます。 アダプターの構成に応じてハードウェアの更新プログラムは通常、ソフトウェア更新プログラムよりもはるかに高速です。  
  
|画面のピクセル形式|Windows Vista、WDDM および 9Ex|その他の Windows Vista の構成|Windows XP SP3 または SP2 と修正プログラム|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (lockable されません)|**ハードウェアの更新**|ソフトウェアの更新|ソフトウェアの更新|ソフトウェアの更新|  
|D3DFMT_X8R8G8B8 (ロック)|**ハードウェアの更新**|ソフトウェアの更新|**ハードウェアの更新**|**ハードウェアの更新**|  
|(ロックではない) では D3DFMT_A8R8G8B8|**ハードウェアの更新**|ソフトウェアの更新|ソフトウェアの更新|ソフトウェアの更新|  
|(ロック) では D3DFMT_A8R8G8B8|**ハードウェアの更新**|ソフトウェアの更新|**ハードウェアの更新**|ソフトウェアの更新|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.D3DImage>
- [WPF と Direct3D9 の相互運用性](wpf-and-direct3d9-interoperation.md)
- [チュートリアル: WPF でホストするための Direct3D9 コンテンツの作成](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [チュートリアル: WPF での Direct3D9 コンテンツをホストしています。](walkthrough-hosting-direct3d9-content-in-wpf.md)
