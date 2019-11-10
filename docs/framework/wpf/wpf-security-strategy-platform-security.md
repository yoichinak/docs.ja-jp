---
title: WPF のセキュリティ方針 - プラットフォーム セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
ms.openlocfilehash: 9c237c06de1388de4c1fe6a6edb3fb5b52522d1f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424631"
---
# <a name="wpf-security-strategy---platform-security"></a>WPF のセキュリティ方針 - プラットフォーム セキュリティ
Windows Presentation Foundation (WPF) にはさまざまなセキュリティサービスが用意されていますが、オペレーティングシステム、CLR、Internet Explorer など、基になるプラットフォームのセキュリティ機能も活用されています。 これらの層を組み合わせることで、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] に強力な多重防御のセキュリティ モデルが提供されます。このセキュリティ モデルでは、次の図に示すように、単一障害点の回避を試みます。  
  
 ![WPF のセキュリティモデルを示す図。](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 このトピックの残りの部分では、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] に関連するこれらの各層の機能について具体的に説明します。  

## <a name="operating-system-security"></a>オペレーティング システムのセキュリティ  
Windows のコアには、WPF を使用して構築されたものを含め、すべての Windows アプリケーションのセキュリティ基盤を形成するセキュリティ機能がいくつか用意されています。 このトピックでは、WPF にとって重要なセキュリティ機能の広範について説明します。また、WPF を統合してさらに多層防御を実現する方法についても説明します。  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Windows の一般的なレビューと強化に加えて、このトピックで説明する [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] には、次の3つの重要な機能があります。  
  
- /GS のコンパイル  
  
- Microsoft Windows Update。  
  
#### <a name="gs-compilation"></a>/GS のコンパイル  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] は、CLR などの [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] のすべての依存関係を含む多数のコアシステムライブラリを再コンパイルすることにより、バッファーオーバーランを軽減します。 これは、C や C++ のコマンド ライン コンパイラの /GS パラメーターを使用して実現されます。 バッファー オーバーランを明示的に避ける必要はありますが、/GS コンパイルは、故意であるかないかにかかわらずバッファー オーバーランによって生み出される潜在的な脆弱性に対する多重防御の一例となります。  
  
 従来、バッファー オーバーランは、影響が大きいセキュリティ攻撃の多くの原因となっていました。 バッファー オーバーランは、バッファーの境界を超えて書き込む、悪意のあるコードの挿入を許すコードの脆弱性を攻撃者が利用するときに発生します。 これにより、攻撃者はプロセスを乗っ取ることができます。この場合、コードは、攻撃者のコードを実行するように関数のリターン アドレスを上書きすることで実行されます。 結果として、乗っ取ったプロセスと同じ特権を持つ任意のコードを実行する悪意のあるコードが生成されます。  
  
 大まかに言えば、-GS コンパイラフラグは、ローカル文字列バッファーを持つ関数のリターンアドレスを保護する特殊なセキュリティクッキーを挿入することによって、潜在的なバッファーオーバーランから保護します。 関数が返されると、セキュリティ クッキーはその前の値と比較されます。 値が変更されている場合、バッファー オーバーランが発生した可能性があるとして、プロセスはエラー状態によって停止されます。 プロセスの停止により、悪意のある可能性があるコードの実行を防止できます。 詳細については[、「-GS (バッファーセキュリティチェック)](/cpp/build/reference/gs-buffer-security-check) 」を参照してください。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、/GS フラグでコンパイルされて、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションに別の防御層を追加します。  
  
### <a name="windows-vista"></a>Windows Vista  
Windows Vista の WPF ユーザーは、"最小限の特権を持つユーザーアクセス"、コードの整合性チェック、および特権の分離など、オペレーティングシステムの追加のセキュリティ強化の恩恵を受けられます。  
  
#### <a name="user-account-control-uac"></a>ユーザー アカウント制御 [UAC]  
 現在、Windows ユーザーは管理者特権で実行される傾向があります。これは、多くのアプリケーションでインストールまたは実行のいずれかまたは両方を行う必要があるためです。 既定のアプリケーションの設定をレジストリに書き込めることが、その一例です。  
  
 管理者特権で実行することの本当の意味は、管理者特権を付与されているプロセスからアプリケーションを実行することです。 これによるセキュリティへの影響は、管理者特権で実行するプロセスを乗っ取る悪意のあるコードが、重要なシステム リソースへのアクセスなど、これらの権限を自動的に継承することです。  
  
 このセキュリティの脅威から保護するための 1 つの方法は、必要最小限の特権でアプリケーションを実行することです。 これは、最小限の特権の原則として知られており、Windows オペレーティングシステムの中核となる機能です。 この機能は、ユーザーアカウント制御 (UAC) と呼ばれ、Windows UAC では次の2つの主要な方法で使用されます。  
  
- ユーザーが管理者であっても、既定で UAC 特権を持つほとんどのアプリケーションを実行するために、管理者特権を必要とするアプリケーションのみが管理者特権で実行されます。 管理者特権で実行するためには、アプリケーションは、アプリケーション マニフェストで、またはセキュリティ ポリシーのエントリとして明示的にマークされる必要があります。  
  
- 仮想化のような互換性に関する解決策を提供します。 たとえば、多くのアプリケーションが C:\Program Files のような制限された場所への書き込みを試みるなどです。 UAC の下で実行するアプリケーションでは、書き込みに管理者特権が必要でない、ユーザーごとの代替の場所が存在します。 UAC の下で実行するアプリケーションでは、UAC は C:\Program Files を仮想化して、書き込もうとしているアプリケーションが、実際はユーザーごとの代替の場所に書き込むようにします。 このような互換性の作業により、オペレーティング システムは、以前は UAC で実行できなかった多くのアプリケーションを実行できるようになります。  
  
#### <a name="code-integrity-checks"></a>コードの整合性チェック  
 Windows Vista には、読み込み時または実行時に悪意のあるコードがシステムファイルやカーネルに挿入されないようにするための、より詳細なコード整合性チェックが組み込まれています。 これは、システム ファイルの保護を超えて動作します。  
   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>ブラウザーでホストされるアプリケーションの制限付き権限のプロセス  
 ブラウザーでホストされる [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションは、インターネット ゾーンのサンド ボックス内で実行します。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Microsoft Internet Explorer との統合により、この保護が追加のサポートで拡張されます。  
  
 一般に、XAML ブラウザーアプリケーション (Xbap) はインターネットゾーンのアクセス許可セットによってサンドボックス化されるため、これらの特権を削除しても、互換性の観点からは、XAML ブラウザーアプリケーション (Xbap) に害はありません。 代わりに、追加の多重防御層が作成されます。セキュリティで保護されたアプリケーションが他のレイヤーを利用してプロセスを乗っ取ることができる場合、プロセスの特権は制限されたままとなります。  
  
 「[最小特権のユーザーアカウントを使用](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29)する」を参照してください。  
  
## <a name="common-language-runtime-security"></a>共通言語ランタイムのセキュリティ  
 共通言語ランタイム (CLR) は、検証と検証、コードアクセスセキュリティ (CAS)、およびセキュリティクリティカルな方法論など、多くの重要なセキュリティ上の利点を提供します。  
    
### <a name="validation-and-verification"></a>確認と検証  
 アセンブリの分離と整合性を提供するために、CLR は検証プロセスを使用します。 CLR 検証では、アセンブリの外部をポイントするアドレスのポータブル実行可能 (PE) ファイル形式を検証することによって、アセンブリが分離されていることを確認します。 CLR 検証では、アセンブリ内に埋め込まれているメタデータの整合性も検証されます。  
  
 型の安全性を確保し、一般的なセキュリティの問題 (バッファーオーバーランなど) を防止し、サブプロセスの分離を通じてサンドボックスを有効にするために、CLR セキュリティでは検証の概念を使用します。  
  
 マネージド アプリケーションは、Microsoft Intermediate Language (MSIL) にコンパイルされます。 マネージド アプリケーション内のメソッドを実行する際、その MSIL は Just-In-Time (JIT) コンパイルを通じてネイティブ コードにコンパイルされます。 JIT コンパイルには、コードが以下を行わないようにする多数の安全性と堅牢性ルールを適用する検証プロセスがあります。  
  
- 型のコントラクトの違反  
  
- バッファー オーバーランの導入  
  
- 乱暴なメモリへのアクセス  
  
 マネージド コードが信頼されたコードと見なされない限り、検証ルールに適合しないマネージド コードの実行は許可されません。  
  
 検証可能なコードの利点は、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] が .NET Framework 上に構築される主な理由です。 検証可能なコードを使用する範囲で、起こりうる脆弱性の悪用の可能性が大幅に減少します。  
  
### <a name="code-access-security"></a>コード アクセス セキュリティ  
 クライアント コンピューターは、ファイル システム、レジストリ、印刷サービス、ユーザー インターフェイス、リフレクション、および環境変数など、マネージド アプリケーションがアクセスできる多種多様なリソースを公開します。 マネージアプリケーションがクライアントコンピューター上のリソースにアクセスできるようにするには、そのアプリケーションに対して .NET Framework アクセス許可を持っている必要があります。 CA のアクセス許可は、<xref:System.Security.CodeAccessPermission> のサブクラスです。CAS は、マネージアプリケーションがアクセスできるリソースごとに1つのサブクラスを実装します。  
  
 管理対象アプリケーションが実行を開始するときに CA によって付与されるアクセス許可のセットは、アクセス許可セットと呼ばれ、アプリケーションによって提供される証拠によって決定されます。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションでは、提供される証拠は、アプリケーションが起動される場所またはゾーンです。 CA は次のゾーンを識別します。  
  
- **マイ コンピューター**。 クライアント コンピューターから起動するアプリケーション (完全信頼)。  
  
- **ローカル イントラネット**。 イントラネットから起動するアプリケーション。 (部分信頼)。  
  
- **インターネット**。 インターネットから起動するアプリケーション。 (最小信頼)。  
  
- **信頼済みサイト**。 ユーザーから信頼すると特定されたアプリケーション。 (最小信頼)。  
  
- **信頼されないサイト**。 ユーザーから信頼しないと特定されたアプリケーション。 (非信頼)。  
  
 これらの各ゾーンに対して、CA は、それぞれに関連付けられている信頼のレベルに一致するアクセス許可を含む定義済みのアクセス許可セットを提供します。 次の設定があります。  
  
- **FullTrust**。 **マイコンピューター**ゾーンから起動するアプリケーションの場合。 可能性のあるすべてのアクセス許可が付与されます。  
  
- **LocalIntranet**。 **ローカルイントラネット**ゾーンから起動するアプリケーションの場合。 分離ストレージ、UI の無制限のアクセス、制約のないファイル ダイアログ、制限付きのリフレクション、環境変数へのアクセス制限など、クライアント コンピューターのリソースへの中程度のアクセスを提供するアクセス許可のサブセットが付与されます。 レジストリのような重要なリソースに対するアクセス許可は提供されません。  
  
- **インターネット**。 **インターネット**または**信頼済みサイト**ゾーンから起動するアプリケーションの場合。 分離ストレージ、ファイルを開くのみ、および制限付きの UI など、クライアント コンピューターに制限付きのアクセス権を付与するため、アクセス許可のサブセットを付与します。 基本的に、このアクセス許可セットは、アプリケーションをクライアントコンピューターから分離します。  
  
 信頼されていない**サイト**ゾーンからのものとして識別されたアプリケーションには、ca によってまったくアクセス許可が付与されません。 その結果、定義済みのアクセス許可セットは存在しません。  
  
 次の図は、ゾーン、アクセス許可セット、アクセス許可、およびリソース間の関係を示しています。  
  
 ![CAS アクセス許可セットを示す図。](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 インターネットゾーンのセキュリティサンドボックスの制限は、XBAP がシステムライブラリからインポートするコード ([!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]を含む) にも同様に適用されます。 これにより、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] であっても、コードはビットごとにロック ダウンされます。 残念ながら、実行できるようにするために、XBAP は、インターネットゾーンのセキュリティサンドボックスで有効になっているものよりも多くのアクセス許可を必要とする機能を実行する必要があります。  
  
 次のページを含む XBAP アプリケーションを考えてみましょう。  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 この XBAP を実行するには、基になる [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] コードが、次のように、呼び出し元の XBAP で使用できるよりも多くの機能を実行する必要があります。  
  
- レンダリング用のウィンドウハンドル (HWND) の作成  
  
- メッセージのディスパッチ  
  
- Tahoma フォントの読み込み  
  
 セキュリティの観点から、セキュリティで保護されたアプリケーションからこれらの操作のいずれかに直接アクセスを許可すると、致命的な状態になります。  
  
 幸い、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、セキュリティで保護されたアプリケーションの代わりに、これらの操作が昇格した特権で実行できるようにすることで、この状況に対応します。 すべての [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 操作は、XBAP のアプリケーションドメインの限られたインターネットゾーンのセキュリティアクセス許可に対してチェックされますが、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (他のシステムライブラリと同様) には、可能なすべてのアクセス許可を含むアクセス許可セットが付与されます。
  
 そのためには、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] が昇格した特権を受け取る一方、それらの特権がホスト アプリケーション ドメインのインターネット ゾーンのアクセス許可セットによって制御されないようにする必要があります。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、アクセス許可の**Assert**メソッドを使用してこれを行います。 次のコードは、その方法を示しています。  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **アサート**は基本的に、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] が XBAP のインターネットゾーンのアクセス許可によって制限される無制限のアクセス許可を禁止します。  
  
 プラットフォームの観点からは、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は**Assert**を正しく使用する役割を担います。**Assert**の不適切な使用により、悪意のあるコードが特権を昇格させる可能性があります。 そのため、必要な場合にのみ**Assert**を呼び出し、サンドボックスの制限をそのまま維持することが重要です。 たとえば、セキュリティで保護されたコードでは、ランダムなファイルを開くことはできませんが、フォントは使用できます。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] を使用すると、サンドボックスアプリケーションは、 **Assert**を呼び出すことによってフォント機能を使用できます。また、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、サンドボックス化されたアプリケーションの代わりにそれらのフォントが含まれていることがわかっている  
  
### <a name="clickonce-deployment"></a>ClickOnce の配置  
 ClickOnce は .NET Framework に含まれる包括的な配置テクノロジで、Visual Studio と統合されています (詳細については、「 [clickonce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください)。 スタンドアロン [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションは ClickOnce を使用して配置できますが、ブラウザーでホストされるアプリケーションは ClickOnce で配置する必要があります。  
  
 ClickOnce を使用してデプロイされたアプリケーションには、コードアクセスセキュリティ (CAS) に対する追加のセキュリティレイヤーが与えられます。基本的に、ClickOnce によって配置されたアプリケーションは、必要なアクセス許可を要求します。 これらのアプリケーションが、アプリケーションの配置元ゾーンのアクセス許可セット数を超えていない場合、これらのアプリケーションには必要なアクセス許可のみが付与されます。 起動ゾーンのアクセス許可セットによって提供されるアクセス許可よりも小さい場合でも、必要なアクセス許可だけを減らすことで、アプリケーションがアクセスできるリソースの数が最小限に抑えられます。 その結果、アプリケーションが乗っ取られた場合、クライアント コンピューターの損傷の可能性が低減します。  
  
### <a name="security-critical-methodology"></a>セキュリティ クリティカルな方法  
 XBAP アプリケーションのインターネットゾーンサンドボックスを有効にするためのアクセス許可を使用する [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] コードは、可能な限り高いレベルのセキュリティ監査と制御に保持する必要があります。 この要件を容易にするために、.NET Framework では、特権を昇格するコードを管理するための新しいサポートを提供しています。 具体的には、CLR を使用すると、特権を昇格するコードを識別し、<xref:System.Security.SecurityCriticalAttribute> でマークすることができます。<xref:System.Security.SecurityCriticalAttribute> でマークされていないコードは、この方法論を使用して*透過的*になります。 逆に、<xref:System.Security.SecurityCriticalAttribute> でマークされていないマネージド コードは特権の昇格ができなくなります。  
  
 セキュリティクリティカルな方法では、*セキュリティクリティカルなカーネル*に特権を昇格する [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] コードの編成が可能になり、残りの部分は透過的になります。 セキュリティクリティカルなコードを分離することにより、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] エンジニアリングチームは、セキュリティクリティカルなカーネルで、標準的なセキュリティプラクティスを上回るセキュリティ分析とソース管理を重視できます (「 [WPF のセキュリティ方針-セキュリティ」を参照してください)。エンジニアリング](wpf-security-strategy-security-engineering.md))。  
  
 .NET Framework では、開発者が <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) でマークされ、ユーザーのグローバルアセンブリキャッシュ (GAC) に展開されたマネージアセンブリを記述できるようにすることで、信頼できるコードが XBAP インターネットゾーンサンドボックスを拡張できることに注意してください。 アセンブリを APTCA でマークすることは、機密性の高いセキュリティ操作です。インターネットからの悪意のあるコードなど、いずれのコードもそのアセンブリを呼び出すことができるためです。 これを実施する際は十分注意し、ベスト プラクティスを使用する必要があります。ソフトウェアをインストールするためには、ユーザーがそのソフトウェアを信頼することを選択する必要があります。  
  
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer のセキュリティ  
 Microsoft Internet Explorer 6 (SP2) には、セキュリティの問題を減らし、セキュリティの構成を簡素化するだけではありませんが、XAML ブラウザーアプリケーション (Xbap) のユーザーのセキュリティを強化するセキュリティが強化された機能がいくつかあります。 これらの機能の推進により、ユーザーが閲覧の制御を拡大できるようにしています。  
  
 IE6 SP2 より前では、ユーザーは次のいずれかの影響を受ける可能性がありました。  
  
- ランダムなポップアップ ウィンドウ。  
  
- スクリプトのリダイレクトの混乱。  
  
- 一部の Web サイトでの多数のセキュリティ ダイアログ。  
  
 場合によっては、信頼されていない Web サイトは、ユーザーがキャンセルした場合でも、インストール [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] をスプーフィングするか、Microsoft ActiveX のインストールダイアログボックスを繰り返し表示することによって、ユーザーのトリックを試みます。 これらの方法によって、大多数のユーザーが騙されて不適切な判断を行い、スパイウェア アプリケーションのインストールにつながる可能性があります。  
  
 IE6 SP2 には、ユーザーによる開始の概念を中心とした、こうした種類の問題を軽減するための機能がいくつか用意されています。 ユーザーがアクションの前にリンクまたはページ要素をクリックしたことがユーザーによって検出された場合 (*ユーザーの開始*と呼ばれます)、ページ上のスクリプトによって同様のアクションがトリガーされる場合とは異なる方法で処理されます。 たとえば、IE6 SP2 には、ページがポップアップを作成する前にユーザーがボタンをクリックしたことを検出する**ポップアップブロック**が組み込まれています。 これにより、ユーザーが要求したり希望したりしないポップアップを防止しながら、ほとんど無害なポップアップを許可することができます。 ブロックされたポップアップは、新しい**情報バー**の下にトラップされます。これにより、ユーザーは手動でブロックをオーバーライドしてポップアップを表示できます。  
  
 また、同じユーザー開始ロジックも適用され、セキュリティプロンプトを**保存 / 保存** **します**。 ActiveX インストールのダイアログボックスは、以前にインストールされたコントロールからのアップグレードを表す場合を除き、常に情報バーの下にトラップされます。 これらの対策を組み合わせると、より安全かつ制御されたユーザー エクスペリエンスがユーザーに提供されます。ユーザーを攻撃して不要または悪意のあるソフトウェアをインストールさせるサイトからユーザーが保護されるためです。  
  
 また、これらの機能により、IE6 SP2 を使用しているお客様は、web サイトを参照して [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションをダウンロードしてインストールできるようになります。 これは特に、IE6 SP2 ではユーザーエクスペリエンスが向上しているため、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]の構築に使用されたテクノロジに関係なく、悪意のあるアプリケーションや不正なアプリケーションをユーザーがインストールする機会が減ります。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、ClickOnce を使用してこれらの保護を強化し、インターネット経由でのアプリケーションのダウンロードを容易にします。 XAML ブラウザーアプリケーション (Xbap) は、インターネットゾーンのセキュリティサンドボックス内で実行されるため、シームレスに起動することができます。 一方、スタンドアロンの [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションでは、実行するには完全な信頼が必要になります。 これらのアプリケーションの場合、ClickOnce は起動プロセス中にセキュリティダイアログボックスを表示して、アプリケーションの追加のセキュリティ要件の使用を通知します。 ただし、これはユーザーが開始する必要があり、ユーザーが開始したロジックによって制御されるとともに、キャンセルが可能です。  
  
 Internet Explorer 7 には、セキュリティに対する継続的なコミットメントの一環として、IE6 SP2 のセキュリティ機能が組み込まれ、拡張されています。  
  
## <a name="see-also"></a>関連項目

- [コード アクセス セキュリティ](../misc/code-access-security.md)
- [Security](security-wpf.md)
- [WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)
- [WPF のセキュリティ方針 - セキュリティ エンジニアリング](wpf-security-strategy-security-engineering.md)
