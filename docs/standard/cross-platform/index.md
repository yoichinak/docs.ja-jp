---
title: .NET Framework による複数のプラットフォームの開発
ms.date: 07/18/2018
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2167f74c5d1dd9f49995b6407e65feb474084dc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641439"
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>.NET Framework による複数のプラットフォームの開発

.NET Framework と Visual Studio を使用して、Microsoft プラットフォームと Microsoft 以外のプラットフォームの両方を対象としたアプリを開発できます。
  
## <a name="options-for-cross-platform-development"></a>クロスプラットフォーム開発のオプション

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 複数プラットフォームを対象として開発する場合は、ソース コードやバイナリを共有し、.NET Framework コードと Windows ランタイム API の間で呼び出しを実行できます。  
  
|目的|用途|  
|-----------------------|------------|  
|Windows Phone 8.1 アプリと Windows 8.1 アプリの間でソース コードを共有する|**共有プロジェクト**(Visual Studio 2013 Update 2 でユニバーサル アプリ テンプレート)。<br /><br /> の現在 Visual Basic はサポートされません。<br /># を使用してプラットフォーム固有のコードを分離できます-`if`ステートメント。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [コーディングを開始します。](/windows/uwp/get-started/create-uwp-apps)<br />-   [Visual Studio を使用して、ユニバーサル XAML アプリを構築する](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/)(ブログの投稿)<br />-   [Visual Studio で XAML コンバージド アプリのビルドを使用して](https://channel9.msdn.com/Events/Build/2014/3-591)(ビデオ)|  
|異なるプラットフォームを対象とするアプリ間でバイナリを共有する|**ポータブル クラス ライブラリ プロジェクト**プラットフォームに依存しないコードです。<br /><br /> -この方法は、ビジネス ロジックを実装するコードを通常使用されます。<br />-は、Visual Basic または c# を使用できます。<br />-API のサポートは、プラットフォームによって異なります。<br />の Windows 8.1 および Windows Phone 8.1 を対象ポータブル クラス ライブラリ プロジェクトでは、Windows ランタイム Api と XAML をサポートします。 これらの機能は、古いバージョンのポータブル クラス ライブラリでは使用できません。<br />-必要な場合はインターフェイスまたは抽象クラスを使用してプラットフォーム固有のコードを抽象化できます。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [ポータブル クラス ライブラリ](cross-platform-development-with-the-portable-class-library.md)<br />-   [ポータブル クラス ライブラリの作成作業の方法](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/)(ブログの投稿)<br />-   [MVVM でポータブル クラス ライブラリの使用](using-portable-class-library-with-model-view-view-model.md) <br />-   [複数のプラットフォームを対象とするライブラリのアプリケーション リソース](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.NET portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (Visual Studio 拡張機能)|  
|Windows 8.1 および Windows Phone 8.1 以外のプラットフォームを対象としたアプリの間でソース コードを共有する|**リンクとして追加**機能します。<br /><br /> -この方法は、何らかの理由は共通する両方のアプリが移植できないアプリ ロジックに適しています。 この機能は Visual Basic または Visual C# のコードに使用できます。<br />     たとえば Windows Phone 8 と Windows 8 は Windows ランタイム API を共有しますが、ポータブル クラス ライブラリはこれらのプラットフォームでは Windows ランタイムをサポートしていません。 Windows Phone 8 アプリと、Windows 8 を対象とした Windows ストア アプリの間で共通する Windows ランタイム コードを共有するには、`Add as link` を使用できます。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [リンクとして追加のコードの共有](https://docs.microsoft.com/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [方法: 既存の項目をプロジェクトに追加します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|  
|.NET Framework を使用して Windows ストア アプリを作成するか、または .NET Framework コードから Windows ランタイム API を呼び出します。|**Windows ランタイム Api**から、.NET Framework c# または Visual Basic のコードと Windows ストア アプリを作成する .NET Framework を使用します。 2 つのプラットフォーム間の API の違いについて注意してください。 ただし、これらの違いに対処するためのクラスがあります。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [Windows ストア アプリおよび Windows ランタイム用 .NET framework のサポート](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [Windows ランタイムへの URI の引き渡し](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|  
|Microsoft 以外のプラットフォームに対応した .NET Framework アプリの開発|**ポータブル クラス ライブラリ参照アセンブリ**.NET Framework および Xamarin などの Visual Studio 拡張機能またはサード パーティ製のツール。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [ポータブル クラス ライブラリすべてのプラットフォームで利用可能です。](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (ブログの投稿)<br />-   [Xamarin ドキュメント](/xamarin)|  
|JavaScript および HTML を使用したクロスプラットフォーム開発|**ユニバーサル アプリ テンプレート**Visual Studio 2013 では、Windows 8.1 および Windows Phone 8.1 用 Windows ランタイム Api に対する開発に 2 を更新します。 現在、クロスプラットフォーム アプリを開発するときに .NET Framework API で JavaScript と HTML を使用することはできません。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [JavaScript プロジェクト テンプレート](https://docs.microsoft.com/previous-versions/windows/apps/hh758331%28v=win.10%29)<br />-   [Windows Phone に JavaScript を使用して Windows ランタイム アプリの移植](https://docs.microsoft.com/previous-versions/windows/apps/dn636144%28v=win.10%29)|
