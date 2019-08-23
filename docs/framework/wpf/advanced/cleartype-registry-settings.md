---
title: ClearType レジストリの設定
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: f4b5a0c3764c173afe03adb67fd3df9d17d9fdcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964893"
---
# <a name="cleartype-registry-settings"></a>ClearType レジストリの設定
このトピックでは、WPF アプリケーションで使用される Microsoft ClearType レジストリ設定の概要について説明します。  

<a name="overview"></a>   
## <a name="technology-overview"></a>テクノロジの概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ディスプレイデバイスにテキストを表示するアプリケーションでは、ClearType 機能を使用して読みやすさを向上させます。 ClearType は、によって[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]開発されたソフトウェアテクノロジで、ラップトップの画面、Pocket PC の画面、フラットパネルモニターなど、既存の lcd (液晶ディスプレイ) でのテキストの読みやすさを向上させます。 ClearType は、LCD 画面のすべてのピクセルで個々の垂直色のストライプ要素にアクセスすることによって機能します。 ClearType の詳細については、「 [cleartype の概要](cleartype-overview.md)」を参照してください。  
  
 ClearType を使用してレンダリングされたテキストは、さまざまなディスプレイデバイスで表示すると、大きく異なる場合があります。 たとえば、少数のモニターでは、より一般的な赤、緑、青 ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) の順序ではなく、青、緑、赤の順序でカラーストライプ要素が実装されます。  
  
 ClearType を使用して表示されるテキストは、さまざまな色の区別レベルを持つ個人によって表示される場合に、大幅に異なる表示になることもあります。 他の人よりも色のわずかな違いを見分ける能力に長けている人もいます。  
  
 これらの各ケースでは、各ユーザーに最適な読み取りエクスペリエンスを提供するために、ClearType 機能を変更する必要があります。  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>レジストリ設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType 機能を制御するための4つのレジストリ設定を指定します。  
  
|設定|説明|  
|-------------|-----------------|  
|ClearType レベル|ClearType の色をわかりやすくするレベルについて説明します。|  
|ガンマ レベル|ディスプレイ デバイスのピクセル カラー コンポーネントのレベルを示します。|  
|ピクセル構造|ディスプレイ デバイスのピクセルの配置を示します。|  
|テキストのコントラスト レベル|表示されるテキストのコントラストのレベルを示します。|  
  
 これらの設定には、特定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の ClearType レジストリ設定を参照する方法を認識する外部構成ユーティリティを使用してアクセスできます。 これらの設定は、Windows レジストリエディターを使用して値に直接アクセスすることによって作成または変更することもできます。  
  
 ClearType レジストリ設定が設定されていない場合 (既定の状態)、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは Windows システムパラメーター情報に対してフォントスムージング設定を照会します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
> [!NOTE]
> 表示デバイス名の列挙の詳細について`SystemParametersInfo`は、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数を参照してください。  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType レベル  
 ClearType レベルでは、個人の色の区別と認識に基づいてテキストのレンダリングを調整できます。 場合によっては、ClearType を最高レベルで使用するテキストをレンダリングしても、最適な読み取りエクスペリエンスが得られないことがあります。  
  
 ClearType レベルは、0 ~ 100 の範囲の整数値です。 既定のレベルは100です。これは、ClearType がディスプレイデバイスのカラーストライプ要素の最大機能を使用することを意味します。 ただし、ClearType レベルが0の場合、テキストはグレースケールとしてレンダリングされます。 0 ~ 100 の範囲の ClearType レベルを設定することにより、個人の色の区別に適した中間レベルを作成できます。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ClearType レベルのレジストリ設定の場所は、特定の表示デバイス名に対応する個々のユーザー設定です。  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの表示デバイス名ごとに、 `ClearTypeLevel` DWORD 値が定義されます。 次のスクリーンショットは、ClearType レベルのレジストリエディターの設定を示しています。  
  
 ![レジストリエディターの ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、ClearType の有無にかかわらず、2つのモードのいずれかでテキストを表示します。 ClearType を使用せずにテキストを表示する場合は、グレースケールレンダリングと呼ばれます。  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>ガンマ レベル  
 ガンマ レベルとは、ピクセル値と輝度間の非線形リレーションシップのことです。 ガンマ レベル設定は、ディスプレイ デバイスの物理特性に対応する必要があります。対応していない場合、レンダリング出力にゆがみが発生する場合があります。 たとえば、テキストの表示が広すぎたり狭すぎたりする場合や、色縁がグリフの縦線の端に表示される場合などがあります。  
  
 ガンマ レベルは、1000 から 2200 の範囲の整数値です。 既定のレベルは 1900 です。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ガンマ レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの表示デバイス名ごとに、 `GammaLevel` DWORD 値が定義されます。 次のスクリーンショットは、ガンマ レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリエディターの ClearType ガンマレベル設定](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>ピクセル構造  
 ピクセル構造は、ディスプレイ デバイスを構成するピクセルの種類を示します。 ピクセル構造は、次の 3 種類のいずれかとして定義されます。  
  
|種類|Value|説明|  
|----------|-----------|-----------------|  
|フラット|0|ディスプレイ デバイスにピクセル構造がありません。 つまり、各色の光源がピクセル領域に均等に拡散しています。これは、グレースケール レンダリングと呼ばれます。 標準のディスプレイ デバイスはこのようにして機能します。 表示されるテキストに ClearType が適用されることはありません。|  
|RGB|1|ディスプレイ デバイスのピクセルは、赤、緑、青の順の 3 つのストライプで構成されます。 表示されるテキストに ClearType が適用されます。|  
|BGR|2|ディスプレイ デバイスのピクセルは、青、緑、赤の順の 3 つのストライプで構成されます。 表示されるテキストに ClearType が適用されます。 順序が RGB の場合の逆であることに注目してください。|  
  
 ピクセル構造は、0 から 2 の範囲の整数値に対応します。 既定のレベルは 0 です。これは、フラット ピクセル構造を表します。  
  
> [!NOTE]
> 表示デバイス名の列挙の詳細について`EnumDisplayDevices`は、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数を参照してください。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ピクセル構造のレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの表示デバイス名ごとに、 `PixelStructure` DWORD 値が定義されます。 次のスクリーンショットは、ピクセル構造のレジストリ エディターの設定を示しています。  
  
 ![レジストリエディターの ClearType ガンマレベル設定](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>テキストのコントラスト レベル  
 テキストのコントラスト レベルを設定すると、グリフの縦線の幅に基づいてテキストのレンダリングを調整できます。 テキストのコントラスト レベルは 0 から 6 の範囲の整数値です。整数値を大きくすると、縦線の幅が広くなります。 既定のレベルは 1 です。  
  
### <a name="registry-setting"></a>レジストリ設定  
 テキストのコントラスト レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応する個々のユーザー設定の場所にあります。  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザーの表示デバイス名ごとに、 `TextContrastLevel` DWORD 値が定義されます。 次のスクリーンショットは、テキストのコントラスト レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリエディターの ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>関連項目

- [ClearType の概要](cleartype-overview.md)
- [ClearType アンチエイリアシング](/windows/desktop/gdi/cleartype-antialiasing)
