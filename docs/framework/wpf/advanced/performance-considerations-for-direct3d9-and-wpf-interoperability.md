---
title: Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 02a91c1824c5d6374f37b0af66a3308d33210c4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932493"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項
Direct3D9 コンテンツは、 <xref:System.Windows.Interop.D3DImage>クラスを使用してホストできます。 Direct3D9 コンテンツをホストすると、アプリケーションのパフォーマンスに影響する可能性があります。 このトピックでは、Windows Presentation Foundation (WPF) アプリケーションで Direct3D9 コンテンツをホストするときのパフォーマンスを最適化するためのベストプラクティスについて説明します。 これらのベストプラクティスには、 <xref:System.Windows.Interop.D3DImage> windows Vista、windows XP、マルチモニターを使用しているときに、ベストプラクティスを使用する方法が含まれています。  
  
> [!NOTE]
> これらのベストプラクティスを示すコード例については、「 [WPF と Direct3D9 の相互運用](wpf-and-direct3d9-interoperation.md)」を参照してください。  
  
## <a name="use-d3dimage-sparingly"></a>D3DImage を控えめに使用する  
 <xref:System.Windows.Interop.D3DImage>インスタンスでホストされている Direct3D9 コンテンツは、純粋な Direct3D アプリケーションと同様に高速には表示されません。 サーフェイスをコピーし、コマンドバッファーをフラッシュすることは、コストのかかる操作になる可能性があります。 インスタンスの<xref:System.Windows.Interop.D3DImage>数が増えるにつれて、より多くのフラッシュが発生し、パフォーマンスが低下します。 このため、控えめを<xref:System.Windows.Interop.D3DImage>使用する必要があります。  
  
## <a name="best-practices-on-windows-vista"></a>Windows Vista のベストプラクティス  
 Windows Vista で windows display Driver Model (WDDM) を使用するように構成されたディスプレイで最適なパフォーマンスを得るには、 `IDirect3DDevice9Ex`デバイスに Direct3D9 surface を作成します。 これにより、サーフェイスの共有が可能になります。 ビデオカードは、Windows Vista `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`の`D3DCAPS2_CANSHARERESOURCE`ドライバーとドライバーの機能をサポートしている必要があります。 それ以外の設定では、ソフトウェアによってサーフェイスがコピーされるため、パフォーマンスが大幅に低下します。  
  
> [!NOTE]
> Windows XP Display Driver Model (XDDM) を使用するように構成されているディスプレイが Windows Vista にある場合は、設定に関係なく、常にソフトウェアを通じてサーフェイスがコピーされます。 適切な設定とビデオカードを使用すると、WDDM を使用した場合のパフォーマンスが向上します。これは、surface のコピーがハードウェアで実行されるためです。  
  
## <a name="best-practices-on-windows-xp"></a>Windows XP のベストプラクティス  
 Windows xp Display Driver Model (xddm) を使用する windows xp で最適なパフォーマンスを得るには、 `IDirect3DSurface9::GetDC`メソッドが呼び出されたときに正しく動作するロック可能なサーフェイスを作成します。 内部的に`BitBlt`は、メソッドはハードウェア内のデバイス間でサーフェイスを転送します。 この`GetDC`メソッドは、常に xrgb サーフェイスで機能します。 ただし、クライアントコンピューターで Windows XP SP3 または SP2 が実行されており、クライアントにレイヤードウィンドウ機能の修正プログラムも含まれている場合、この方法は ARGB サーフェイスでのみ機能します。 ビデオカードは、ドライバーの`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`機能をサポートしている必要があります。  
  
 16ビットデスクトップの表示深度を使用すると、パフォーマンスが大幅に低下する可能性があります。 32ビットのデスクトップをお勧めします。  
  
 Windows Vista および Windows XP 向けに開発している場合は、Windows XP でパフォーマンスをテストします。 Windows XP でビデオメモリが不足している場合は、問題があります。 さらに、 <xref:System.Windows.Interop.D3DImage> windows XP では、必要な追加のビデオメモリコピーにより、windows Vista WDDM よりも多くのビデオメモリと帯域幅が使用されます。 そのため、windows Vista では、同じビデオハードウェアのパフォーマンスが低下することが予想されます。  
  
> [!NOTE]
> XDDM は Windows XP と Windows Vista の両方で使用できます。ただし、WDDM は Windows Vista でのみ使用できます。  
  
## <a name="general-best-practices"></a>一般的なベストプラクティス  
 デバイスを作成するときは、 `D3DCREATE_MULTITHREADED`作成フラグを使用します。 これにより、パフォーマンスが低下しますが、WPF レンダリングシステムは、このデバイスのメソッドを別のスレッドから呼び出します。 2つのスレッドが同時にデバイスにアクセスしないように、必ずロックプロトコルに従ってください。  
  
 WPF マネージスレッドでレンダリングを実行する場合は、 `D3DCREATE_FPU_PRESERVE`作成フラグを使用してデバイスを作成することを強くお勧めします。 この設定がないと、D3D レンダリングにより、WPF の倍精度演算の精度が低下し、レンダリングの問題が発生する可能性があります。  
  
 ハードウェアを<xref:System.Windows.Interop.D3DImage>サポートせずに pow2 表面を並べていない場合、またはを含む<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>を並べて表示し<xref:System.Windows.Interop.D3DImage>ている場合を除き、のタイルが高速になります。  
  
## <a name="best-practices-for-multi-monitor-displays"></a>マルチモニター表示のベストプラクティス  
 複数のモニターが搭載されたコンピューターを使用している場合は、前述のベストプラクティスに従う必要があります。 マルチモニター構成には、さらにパフォーマンスに関する考慮事項もいくつかあります。  
  
 バックバッファーを作成すると、そのバッファーは特定のデバイスとアダプターに作成されますが、WPF によってアダプターのフロントバッファーが表示されることがあります。 アダプター間でコピーを行ってフロントバッファーを更新すると、非常に負荷が大きくなる可能性があります。 複数のビデオカードおよび`IDirect3DDevice9Ex`デバイスで WDDM を使用するように構成されている Windows Vista では、フロントバッファーが別のアダプターにあり、同じビデオカードを使用している場合、パフォーマンスが低下することはありません。 ただし、Windows XP および複数のビデオカードを使用した XDDM では、フロントバッファーがバックバッファーとは別のアダプターに表示される場合、パフォーマンスが大幅に低下します。 詳細については、「 [WPF と Direct3D9 の相互運用](wpf-and-direct3d9-interoperation.md)」を参照してください。  
  
## <a name="performance-summary"></a>パフォーマンスの概要  
 次の表は、オペレーティングシステム、ピクセル形式、および surface lockability の機能としてのフロントバッファー更新のパフォーマンスを示しています。 フロントバッファーとバックバッファーは同じアダプター上にあると見なされます。 アダプターの構成によっては、通常、ソフトウェア更新プログラムよりもハードウェアの更新がはるかに高速になります。  
  
|サーフェイスのピクセル形式|Windows Vista、WDDM、および9Ex|その他の Windows Vista の構成|Windows XP SP3 または SP2 (修正プログラム)|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (ロックできません)|**ハードウェアの更新**|ソフトウェア更新プログラム|ソフトウェア更新プログラム|ソフトウェア更新プログラム|  
|D3DFMT_X8R8G8B8 (ロック可能)|**ハードウェアの更新**|ソフトウェア更新プログラム|**ハードウェアの更新**|**ハードウェアの更新**|  
|D3DFMT_A8R8G8B8 (ロックできません)|**ハードウェアの更新**|ソフトウェア更新プログラム|ソフトウェア更新プログラム|ソフトウェア更新プログラム|  
|D3DFMT_A8R8G8B8 (ロック可能)|**ハードウェアの更新**|ソフトウェア更新プログラム|**ハードウェアの更新**|ソフトウェア更新プログラム|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.D3DImage>
- [WPF と Direct3D9 の相互運用性](wpf-and-direct3d9-interoperation.md)
- [チュートリアル: WPF でホストするための Direct3D9 コンテンツの作成](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [チュートリアル: WPF での Direct3D9 コンテンツのホスト](walkthrough-hosting-direct3d9-content-in-wpf.md)
