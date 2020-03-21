---
title: ClearType レジストリの設定
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: bedd99fcf9b4ca1d10b4c24d7cff9de320e6fd12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186176"
---
# <a name="cleartype-registry-settings"></a>ClearType レジストリの設定
このトピックでは、WPF アプリケーションで使用される Microsoft ClearType レジストリ設定の概要を説明します。  

<a name="overview"></a>
## <a name="technology-overview"></a>テクノロジの概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]表示デバイスにテキストをレンダリングするアプリケーションでは、ClearType 機能を使用して読み取りエクスペリエンスを向上させます。 ClearType は、ラップトップの画面、ポケット PC 画面、フラット パネル モニターなどの既存の LCD (液晶ディスプレイ) 上のテキストの読みやすさを向上させるマイクロソフトが開発したソフトウェア テクノロジです。 ClearType は、LCD 画面の各ピクセルの縦色のストライプ要素に個別にアクセスすることで機能します。 ClearType の詳細については、「 [ClearType の概要](cleartype-overview.md)」を参照してください。  
  
 ClearType でレンダリングされるテキストは、さまざまなディスプレイ デバイスで表示すると、大きく異なる表示ができます。 たとえば、少数のモニタでは、赤、緑、青 (RGB) の順序ではなく、青色、緑、赤の順序でカラー ストライプ要素が実装されます。  
  
 ClearType でレンダリングされるテキストは、色の感度のレベルが異なる個人が表示した場合にも、大きく異なる表示ができます。 他の人よりも色のわずかな違いを見分ける能力に長けている人もいます。  
  
 いずれの場合も、個々のユーザーに最適な読み取りエクスペリエンスを提供するために、ClearType 機能を変更する必要があります。  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>レジストリ設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、ClearType 機能を制御するための 4 つのレジストリ設定を指定します。  
  
|設定|説明|  
|-------------|-----------------|  
|型のクリア レベル|ClearType の色の明瞭度のレベルを説明します。|  
|ガンマ レベル|ディスプレイ デバイスのピクセル カラー コンポーネントのレベルを示します。|  
|ピクセル構造|ディスプレイ デバイスのピクセルの配置を示します。|  
|テキストのコントラスト レベル|表示されるテキストのコントラストのレベルを示します。|  
  
 これらの設定には、特定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]された ClearType レジストリ設定の参照方法を知っている外部構成ユーティリティからアクセスできます。 これらの設定は、Windows レジストリ エディタを使用して値に直接アクセスすることによって作成または変更することもできます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType レジストリ設定が設定されていない場合 (既定の状態)、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、フォント スムージング設定の Windows システム パラメーター情報を照会します。  
  
> [!NOTE]
> ディスプレイ デバイス名の列挙については、Win32`SystemParametersInfo`関数を参照してください。  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a>ClearType レベル  
 ClearType レベルでは、個々の色の感度と知覚に基づいてテキストのレンダリングを調整できます。 一部のユーザーにとって、ClearType を使用するテキストを最高レベルでレンダリングしても、最適な読み取りエクスペリエンスが得られない場合があります。  
  
 ClearType レベルは、0 ~ 100 の範囲の整数値です。 デフォルトレベルは 100 で、ClearType はディスプレイ デバイスのカラー ストライプ要素の最大機能を使用します。 ただし、ClearType レベル 0 の場合は、テキストがグレースケールとしてレンダリングされます。 ClearType レベルを 0 ~ 100 の間で設定すると、個人の色の区別に適した中間レベルを作成できます。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ClearType レベルのレジストリ設定の場所は、特定のディスプレイ デバイス名に対応する個々のユーザー設定です。  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの各ディスプレイ デバイス名に対して`ClearTypeLevel`、DWORD 値が定義されます。 次のスクリーンショットは、ClearType レベルのレジストリ エディタ設定を示しています。  
  
 ![レジストリ エディタの ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、ClearType の有無にかかわらず、2 つのモードのいずれかでテキストをレンダリングします。 ClearType を使用せずにテキストをレンダリングする場合、そのテキストはグレー スケール レンダリングと呼ばれます。  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a>ガンマ レベル  
 ガンマ レベルとは、ピクセル値と輝度間の非線形リレーションシップのことです。 ガンマ レベル設定は、ディスプレイ デバイスの物理特性に対応する必要があります。対応していない場合、レンダリング出力にゆがみが発生する場合があります。 たとえば、テキストが広すぎたり狭すぎたり、グリフの垂直幹の端に色のフリンジが表示されたりすることがあります。  
  
 ガンマ レベルは、1000 から 2200 の範囲の整数値です。 既定のレベルは 1900 です。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ガンマ レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの各ディスプレイ デバイス名に対して`GammaLevel`、DWORD 値が定義されます。 次のスクリーンショットは、ガンマ レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディタの ClearType ガンマ レベル設定](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a>ピクセル構造  
 ピクセル構造は、ディスプレイ デバイスを構成するピクセルの種類を示します。 ピクセル構造は、次の 3 種類のいずれかとして定義されます。  
  
|Type|Value|説明|  
|----------|-----------|-----------------|  
|フラット|0|ディスプレイ デバイスにピクセル構造がありません。 つまり、各色の光源がピクセル領域に均等に拡散しています。これは、グレースケール レンダリングと呼ばれます。 標準のディスプレイ デバイスはこのようにして機能します。 ClearType は、レンダリングされたテキストには適用されません。|  
|RGB|1|ディスプレイ デバイスのピクセルは、赤、緑、青の順の 3 つのストライプで構成されます。 レンダリングされたテキストに ClearType が適用されます。|  
|BGR|2|ディスプレイ デバイスのピクセルは、青、緑、赤の順の 3 つのストライプで構成されます。 レンダリングされたテキストに ClearType が適用されます。 順序が RGB の場合の逆であることに注目してください。|  
  
 ピクセル構造は、0 から 2 の範囲の整数値に対応します。 既定のレベルは 0 です。これは、フラット ピクセル構造を表します。  
  
> [!NOTE]
> ディスプレイ デバイス名の列挙については、Win32`EnumDisplayDevices`関数を参照してください。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ピクセル構造のレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの各ディスプレイ デバイス名に対して`PixelStructure`、DWORD 値が定義されます。 次のスクリーンショットは、ピクセル構造のレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディタの ClearType ガンマ レベル設定](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a>テキストのコントラスト レベル  
 テキストのコントラスト レベルを設定すると、グリフの縦線の幅に基づいてテキストのレンダリングを調整できます。 テキストのコントラスト レベルは 0 から 6 の範囲の整数値です。整数値を大きくすると、縦線の幅が広くなります。 既定のレベルは 1 です。  
  
### <a name="registry-setting"></a>レジストリ設定  
 テキストのコントラスト レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応する個々のユーザー設定の場所にあります。  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの各ディスプレイ デバイス名に対して`TextContrastLevel`、DWORD 値が定義されます。 次のスクリーンショットは、テキストのコントラスト レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディタの ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>関連項目

- [ClearType の概要](cleartype-overview.md)
- [ClearType アンチエイリアシング](/windows/desktop/gdi/cleartype-antialiasing)
