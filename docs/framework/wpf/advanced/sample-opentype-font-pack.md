---
title: OpenType フォント パックのサンプル
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 76438b85a12d75efa0fc106a645fb592b3205fad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960971"
---
# <a name="sample-opentype-font-pack"></a>OpenType フォント パックのサンプル
このトピックでは、 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]で配布されるサンプル OpenType フォントの概要について説明します。 サンプルフォントでは、アプリケーションで[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用できる拡張 OpenType 機能がサポートされています。  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType フォント パックのフォント  
 に[!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]は、アプリケーションの作成[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]に使用できる一連のサンプル OpenType フォントが用意されています。 サンプル フォントは、Ascender Corporation のライセンスを受けて提供されています。 これらのフォントは、OpenType 形式で定義されている合計機能のサブセットのみを実装します。 次の表に、サンプルの OpenType フォントの名前を示します。  
  
|**名前**|**ファイル**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 次の図は、サンプルの OpenType フォントの外観を示しています。  
  
 ![サンプル フォント パック内のフォント名の一覧](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 サンプル フォントは、Ascender Corporation のライセンスを受けて提供されています。 Ascender は、高度なフォント製品を提供する企業です。 サンプル フォントの拡張版またはカスタム版のライセンスを受けるには、[Ascender Corporation の Web サイト](https://go.microsoft.com/fwlink/?LinkId=182627)を参照してください。  
  
> [!NOTE]
> アプリケーションに埋め込む、または別の方法で再頒布するフォントについて、必要なライセンス権限を取得することは、開発者であるユーザーの責任で行ってください。  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>フォントのインストール  
 既定の Windows フォントディレクトリである **\WINDOWS\Fonts**にサンプルの OpenType フォントをインストールするオプションがあります。 フォントをインストールするには、コントロール パネルの [フォント] を使用します。 これらのフォントは、コンピューター上にあると、既定の Windows フォントを参照するすべてのアプリケーションからアクセスできるようになります。 フォント ファイルをダブルクリックして、各フォントの文字を異なるいくつかのフォント サイズで表示できます。 次のスクリーン ショットは、Lindsey フォント ファイル (Linds.ttf) を表示したものです。  
  
 ![Lindsey フォント&#40;OpenType&#41; ](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Lindsey フォントの表示  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>フォントの使用  
 アプリケーションでフォントを使用するには、2 とおりの方法があります。 アセンブリ内にリソースとして埋め込まれていないプロジェクト コンテンツ項目として、フォントをアプリケーションに追加できます。 あるいは、アプリケーションのアセンブリ ファイル内に埋め込まれたプロジェクト リソース項目として、フォントをアプリケーションに追加できます。 詳細については、「[アプリケーションでのフォントのパッケージング](packaging-fonts-with-applications.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Documents.Typography>
- [OpenType フォントの機能](opentype-font-features.md)
- [アプリケーションでのフォントのパッケージング](packaging-fonts-with-applications.md)
