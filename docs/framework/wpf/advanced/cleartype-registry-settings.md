---
title: ClearType レジストリの設定
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: a776c3d4060b9ca291e4e919ab6ca33fb713434c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051391"
---
# <a name="cleartype-registry-settings"></a>ClearType レジストリの設定
このトピックの概要を示します、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]レジストリ設定で使用される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  

<a name="overview"></a>   
## <a name="technology-overview"></a>テクノロジの概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テキスト表示デバイスの使用をレンダリングするアプリケーション[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]機能、強化された閲覧エクスペリエンスを提供します。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] は、ラップトップや Pocket PC の画面、フラット パネル モニターなど、既存の LCD (液晶ディスプレイ) でのテキストの読みやすさを向上させるために [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] が開発したソフトウェア テクノロジです。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] は、LCD 画面の各ピクセル内の個々の垂直カラー ストライプ要素にアクセスすることによって機能します。 詳細については[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]を参照してください[ClearType の概要](cleartype-overview.md)します。  
  
 レンダリングされるテキスト[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]ディスプレイ デバイスで表示したときに大幅に異なる表示されることができます。 青、緑、赤の順でカラー ストライプ要素ではなく、一般的な赤、緑、青のモニターの数が少ないの実装例 ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) の順序。  
  
 レンダリングされるテキスト[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]大きく異なる色の感度のさまざまなレベルを持つ個人によって場合でも表示できます。 他の人よりも色のわずかな違いを見分ける能力に長けている人もいます。  
  
 このような場合は、の各[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]機能が最も読みやすいをごとに提供するために変更する必要があります。  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>レジストリ設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 制御するための 4 つのレジストリ設定の指定[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]機能。  
  
|設定|説明|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベル|レベルを示します[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]わかりやすくするための色します。|  
|ガンマ レベル|ディスプレイ デバイスのピクセル カラー コンポーネントのレベルを示します。|  
|ピクセル構造|ディスプレイ デバイスのピクセルの配置を示します。|  
|テキストのコントラスト レベル|表示されるテキストのコントラストのレベルを示します。|  
  
 これらの設定は、識別されたを参照する方法を認識している外部構成ユーティリティによってアクセスできる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レジストリ設定します。 これらの設定は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] レジストリ エディターを使用して値に直接アクセスして作成または変更することもできます。  
  
 場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レジストリ設定が (これは、既定の状態) を設定されていない、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションのクエリ、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]フォント スムージング設定用システム パラメーター情報。  
  
> [!NOTE]
>  ディスプレイ デバイス名を列挙する方法の詳細については、次を参照してください。、 `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数。  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType レベル  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レベルでは、色の感度と個人の知覚に基づいてテキストのレンダリングを調整できます。 人によっては、テキストのレンダリングを使用する[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]最上位のレベルは生成されませんが最も読みやすい。  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レベルは 0 から 100 の範囲の整数値。 既定のレベルは 100、つまり[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]ディスプレイ デバイスのカラー ストライプ要素の最大の機能を使用します。 ただし、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レベル 0 は、グレースケールとしてテキストを描画します。 設定して、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レベル 0 ~ 100 のどこかに、作成、個人の色の感度に適した中間レベル。  
  
### <a name="registry-setting"></a>レジストリ設定  
 レジストリ設定の場所、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レベルは、特定のディスプレイ デバイス名に対応する個々 のユーザー設定。  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 で、ユーザーのディスプレイ デバイス名ごと、 `ClearTypeLevel` DWORD 値を定義します。 次のスクリーン ショットのレジストリ エディターの設定、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]レベル。  
  
 ![レジストリ エディターの ClearType 設定します。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションで必要に応じて、いずれか 2 つのモードのいずれかのテキストのレンダリング[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]します。 テキストのレンダリングせず[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]、グレースケール レンダリングと呼びます。  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>ガンマ レベル  
 ガンマ レベルとは、ピクセル値と輝度間の非線形リレーションシップのことです。 ガンマ レベル設定は、ディスプレイ デバイスの物理特性に対応する必要があります。対応していない場合、レンダリング出力にゆがみが発生する場合があります。 たとえば、テキストの表示が広すぎたり狭すぎたりする場合や、色縁がグリフの縦線の端に表示される場合などがあります。  
  
 ガンマ レベルは、1000 から 2200 の範囲の整数値です。 既定のレベルは 1900 です。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ガンマ レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 で、ユーザーのディスプレイ デバイス名ごと、 `GammaLevel` DWORD 値を定義します。 次のスクリーンショットは、ガンマ レベルのレジストリ エディターの設定を示しています。  
  
 ![ClearType ガンマ レベルの設定、レジストリ エディター](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>ピクセル構造  
 ピクセル構造は、ディスプレイ デバイスを構成するピクセルの種類を示します。 ピクセル構造は、次の 3 種類のいずれかとして定義されます。  
  
|型|[値]|説明|  
|----------|-----------|-----------------|  
|フラット|0|ディスプレイ デバイスにピクセル構造がありません。 つまり、各色の光源がピクセル領域に均等に拡散しています。これは、グレースケール レンダリングと呼ばれます。 標準のディスプレイ デバイスはこのようにして機能します。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] はレンダリングされたテキストに適用されません。|  
|RGB|1|ディスプレイ デバイスのピクセルは、赤、緑、青の順の 3 つのストライプで構成されます。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] がレンダリングされたテキストに適用されます。|  
|BGR|2|ディスプレイ デバイスのピクセルは、青、緑、赤の順の 3 つのストライプで構成されます。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] がレンダリングされたテキストに適用されます。 順序が RGB の場合の逆であることに注目してください。|  
  
 ピクセル構造は、0 から 2 の範囲の整数値に対応します。 既定のレベルは 0 です。これは、フラット ピクセル構造を表します。  
  
> [!NOTE]
>  ディスプレイ デバイス名を列挙する方法の詳細については、次を参照してください。、 `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数。  
  
### <a name="registry-setting"></a>レジストリ設定  
 ピクセル構造のレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 で、ユーザーのディスプレイ デバイス名ごと、 `PixelStructure` DWORD 値を定義します。 次のスクリーンショットは、ピクセル構造のレジストリ エディターの設定を示しています。  
  
 ![ClearType ガンマ レベルの設定、レジストリ エディター](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>テキストのコントラスト レベル  
 テキストのコントラスト レベルを設定すると、グリフの縦線の幅に基づいてテキストのレンダリングを調整できます。 テキストのコントラスト レベルは 0 から 6 の範囲の整数値です。整数値を大きくすると、縦線の幅が広くなります。 既定のレベルは 1 です。  
  
### <a name="registry-setting"></a>レジストリ設定  
 テキストのコントラスト レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応する個々のユーザー設定の場所にあります。  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 で、ユーザーのディスプレイ デバイス名ごと、 `TextContrastLevel` DWORD 値を定義します。 次のスクリーンショットは、テキストのコントラスト レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディターの ClearType 設定します。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>関連項目

- [ClearType の概要](cleartype-overview.md)
- [ClearType アンチエイリアシング](/windows/desktop/gdi/cleartype-antialiasing)
