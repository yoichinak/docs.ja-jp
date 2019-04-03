---
title: Windows ランタイムへの URI の引き渡し
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5ce0d4ac2b95dc4d51e785e3a00026f56c13d2c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220708"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Windows ランタイムへの URI の引き渡し
Windows ランタイムのメソッドは絶対 URI だけを受け取ります。 [!INCLUDE[wrt](../../../includes/wrt-md.md)] メソッドに相対 URI を渡すと、<xref:System.ArgumentException> 例外がスローされます。 その理由を次に示します: を使用すると、 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 、.NET Framework コードで、<xref:Windows.Foundation.Uri?displayProperty=nameWithType>クラスとして表示されます<xref:System.Uri?displayProperty=nameWithType>Intellisense にします。 <xref:System.Uri?displayProperty=nameWithType>クラスは、相対 Uri を使用できますが、<xref:Windows.Foundation.Uri?displayProperty=nameWithType>クラスはありません。 [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントで公開するメソッドでも同様です。 URI を受け取るメソッドをコンポーネントで公開する場合、コードのシグネチャには <xref:System.Uri?displayProperty=nameWithType> が含まれます。 ただし、コンポーネントのユーザーに、署名は<xref:Windows.Foundation.Uri?displayProperty=nameWithType>します。 コンポーネントに渡す URI は、絶対 URI でなければなりません。  
  
このトピックでは、絶対 URI を検出する方法と、アプリ パッケージ内のリソースを参照するときに絶対 URI を作成する方法を説明します。  
  
## <a name="detecting-and-using-an-absolute-uri"></a>絶対 URI の検出と使用  
URI を <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>に渡す前にそれが絶対 URI であることを確認するには、[!INCLUDE[wrt](../../../includes/wrt-md.md)] プロパティを使用します。 このプロパティを使用する方が、<xref:System.ArgumentException> 例外をキャッチして処理するより効率的です。  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>アプリ パッケージのリソースに対する絶対 URI の使用  
アプリのパッケージに含まれるリソースに対して URI を指定するには、`ms-appx` スキームまたは `ms-appx-web` スキームを使用して絶対 URI を作成します。  
  
次の例は、設定する方法を示します、<xref:Windows.UI.Xaml.Controls.WebView.Source%2A>プロパティを<xref:Windows.UI.Xaml.Controls.WebView>コントロールと<xref:Windows.UI.Xaml.Controls.Image.Source%2A>プロパティを<xref:Windows.UI.Xaml.Controls.Image>XAML とコードの両方を使用して、ページをという名前のフォルダーに格納されているリソースへの制御。  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
これらのスキームの詳細については、[URI スキーム](/windows/uwp/app-resources/uri-schemes)、Windows デベロッパー センターでを参照してください。  
  
## <a name="see-also"></a>関連項目

- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
