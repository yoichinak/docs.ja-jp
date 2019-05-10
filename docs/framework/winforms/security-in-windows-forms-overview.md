---
title: Windows フォームのセキュリティの概要
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: dbbba191f201264f5044de8696518e76a1db42fb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655607"
---
# <a name="security-in-windows-forms-overview"></a>Windows フォームのセキュリティの概要

[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のリリース以前、ユーザーのコンピューターで実行されているすべてのコードは、リソースにアクセスするために、そのコンピューターのユーザーが持っていたのと同じ権限またはアクセス許可を持っていました。 たとえば、ユーザーにファイル システムへのアクセスが許可されている場合は、コードにファイル システムへのアクセスが許可され、ユーザーにデータベースへのアクセスが許可されている場合は、コードにデータベースへのアクセスが許可されていました。 これらの権限やアクセス許可は、ユーザーがローカル コンピューターに明示的にインストールした実行可能ファイルのコードに対しては受け入れることができますが、インターネットやローカル イントラネットからの悪意のある可能性があるコードに対しては受け入れることができません。 このコードは、アクセス許可がないユーザーのコンピューター リソースにアクセスすべきではありません。

[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] は、アクセス許可または権限について、コードが持つものとユーザーが持つものを区別できる、コード アクセス セキュリティと呼ばれるインフラストラクチャを導入しています。 既定では、インターネットとイントラネットからのコードは、部分信頼と呼ばれるものでのみ実行できます。 部分信頼では、アプリケーションに一連の制限が適用されます。特に、アプリケーションはローカルのハード ディスクへのアクセスが制限され、アンマネージ コードを実行することができません。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] は、送信元、[厳密な名前付きアセンブリ](../app-domains/strong-named-assemblies.md)があるかどうか、証明書で署名されているかどうかなど、そのコードの ID に基づいて、コードにアクセスを許可するリソースを制御します。

[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] テクノロジは、Windows フォーム アプリケーションの配置に使用しますが、部分信頼で実行するアプリケーションを、完全信頼や、昇格されたアクセス許可を持つ部分信頼で簡単に開発できるようにします。 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] は、アクセス許可の昇格や、信頼されたアプリケーション配置などの機能を提供し、アプリケーションが完全信頼やアクセス許可の昇格をローカル ユーザーから実行可能な方法で要求できます。

## <a name="understanding-security-in-the-net-framework"></a>.NET Framework のセキュリティについて

コード アクセス セキュリティにより、コードの発生元や、そのコードの身元を示すその他の基準に基づいて、コードをさまざまなレベルで信頼できます。 共通言語ランタイムがセキュリティ ポリシーを決定するために使用する証拠の詳細については、「[証拠](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100))」を参照してください。 悪意のあるコードからコンピューター システムを保護できるだけでなく、セキュリティの意図的または偶然の侵害から信頼されているコードを保護できます。 また、コード アクセス セキュリティは、アプリケーションが実行できるアクションに対して詳細に制御できます。これは、アプリケーションが持っている必要があるアクセス許可のみを指定できるためです。 コード アクセス セキュリティは、コードが単一のコード アクセス セキュリティのアクセス許可のチェックをしない場合でも、共通言語ランタイムを対象とするすべてのマネージド コードに影響を与えます。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のセキュリティの詳細については、「[セキュリティの基本概念](../../standard/security/key-security-concepts.md)」および「[コード アクセス セキュリティの基礎](../misc/code-access-security-basics.md)」を参照してください。

ユーザーが Windows フォームの実行可能ファイルを Web サーバーまたはファイル共有から直接実行する場合、アプリケーションに付与される信頼の度合いは、コードが存在する場所や開始方法によって異なります。 アプリケーションを実行すると、自動的に評価され、共通言語ランタイムから、名前付き権限セットを受け取ります。 既定では、ローカル コンピューターからのコードに完全信頼のアクセス許可セットが付与され、ローカル ネットワークからのコードには、ローカル イントラネットのアクセス許可セットが付与され、インターネットからのコードには、インターネットのアクセス許可セットが付与されます。

> [!NOTE]
> [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] バージョン 1.0 Service Pack 1 と Service Pack 2 では、インターネット ゾーンのコード グループが何もしないアクセス許可セットを受け取ります。 その他のすべてのリリースの [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、インターネット ゾーンのコード グループは、インターネットのアクセス許可セットを受け取ります。
>
> これらの各アクセス許可セットで付与される既定のアクセス許可の一覧については、「[既定のセキュリティ ポリシー](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))」を参照してください。 アプリケーションが受け取るアクセス許可に応じて、正常に実行されるか、またはセキュリティ例外が生成されます。
>
> [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] を使用して、多数の Windows フォーム アプリケーションが配置されます。 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] の配置の生成に使用されるツールには、これまでの説明とは異なるセキュリティの既定値があります。 詳細については、次の説明を参照してください。

アプリケーションに付与される実際のアクセス許可は、セキュリティ ポリシーが変更される可能性があるため、既定値とは異なる可能性があります。つまり、アプリケーションが、あるコンピューターではアクセス許可を持ち、別のコンピューターでは持たない可能性があることを意味します。

## <a name="developing-a-more-secure-windows-forms-application"></a>より安全な Windows フォーム アプリケーションの開発

セキュリティは、アプリケーション開発のすべての手順で重要です。 まず、「[安全なコーディングのガイドライン](../../standard/security/secure-coding-guidelines.md)」を確認し、このガイドラインに従います。

次に、アプリケーションを完全信頼で実行する必要があるのか、または部分信頼で実行する必要があるのかを決定します。 完全信頼でアプリケーションを実行することで、ローカル コンピューター上のリソースへのアクセスが簡単になりますが、「安全なコーディングのガイドライン」のトピックに厳密に従ってアプリケーションを設計および開発しない場合、ユーザーとアプリケーションを高いセキュリティ リスクに晒すことになります。 部分信頼でアプリケーションを実行すると、より安全なアプリケーションをより簡単に開発でき、リスクを大幅に軽減しますが、特定の機能の実装方法について、より詳細な計画が必要になります。

部分信頼 (つまり、インターネットまたはローカル イントラネットのアクセス許可セットのいずれか) を選択する場合は、アプリケーションがこの環境で動作する方法を決定します。 Windows フォームでは、信頼度の低い環境で、より安全に機能を実装する代わりの方法を提供します。 データ アクセスなど、アプリケーションの特定の部分が、部分信頼および完全信頼の両方の環境で異なる設計と作成がなされる場合があります。 アプリケーション設定など、一部の Windows フォームの機能は、部分信頼で動作するよう設計されています。 詳細については、「[アプリケーション設定の概要](./advanced/application-settings-overview.md)」を参照してください。

アプリケーションが部分信頼で許可するより多くのアクセス許可を必要とするが、完全信頼モードで実行したくない場合は、部分信頼で実行しながら、必要な追加のアクセス許可のみをアサートすることができます。 たとえば、部分信頼で実行するが、ユーザーのファイル システム上のディレクトリに、アプリケーションの読み取り専用のアクセス許可を付与する必要がある場合、そのディレクトリのみに対して <xref:System.Security.Permissions.FileIOPermission> を要求することができます。 適切に使用すると、このアプローチによってアプリケーションの機能が増加し、ユーザーのセキュリティ上のリスクを最小限に抑えることができます。

部分信頼で実行されるアプリケーションを開発するときに、アプリケーションが実行する必要があるアクセス許可と、アプリケーションがオプションで使用できるアクセス許可を管理してください。 すべてのアクセス許可がわかっている場合、アプリケーション レベルでアクセス許可について宣言型の要求をする必要があります。 アクセス許可を要求すると、アプリケーションが必要とするアクセス許可、および特に必要ないアクセス許可について、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のランタイムに通知します。 アクセス許可の要求の詳細については、「[アクセス許可の要求](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))」を参照してください。

オプションのアクセス許可を要求するときに、アプリケーションに付与されていないアクセス許可が必要なアクションを実行する場合に生成されるセキュリティ例外を処理する必要があります。 <xref:System.Security.SecurityException> を適切に処理することで、アプリケーションを続行できます。 アプリケーションは例外を使用して、ユーザーに対して機能を無効にする必要があるかどうかを判断できます。 たとえば、必要なファイル アクセス許可が付与されていない場合、アプリケーションは **[保存]** メニュー オプションを無効にすることができます。

場合によっては、すべての適切なアクセス許可をアサートしたかどうかを確認することが難しい場合があります。 たとえば、表面的には影響のないように見えるメソッドの呼び出しが、実行中のある時点でファイル システムにアクセスすることがあります。 必要なアクセス許可をすべて使用してアプリケーションを配置しない場合は、デスクトップでデバッグしている間は問題なくテストでき、配置のときに失敗する可能性があります。 両方の[!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]SDK と Visual Studio 2005 は、アプリケーションに必要なアクセス許可を計算するためのツールを含む: MT.exe のコマンド ライン ツールと Visual Studio でのアクセス許可の検出機能は、それぞれします。

次のトピックでは、Windows フォームの追加のセキュリティ機能について説明します。

|トピック|説明|
|-----------|-----------------|
|- [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](more-secure-file-and-data-access-in-windows-forms.md)|部分信頼環境でファイルとデータにアクセスする方法について説明します。|
|- [Windows フォームでのより安全な印刷](more-secure-printing-in-windows-forms.md)|部分信頼環境で印刷機能にアクセスする方法について説明します。|
|- [Windows フォームのセキュリティに関するその他の考慮事項](additional-security-considerations-in-windows-forms.md)|部分信頼環境でのウィンドウ操作の実行、クリップボードの使用、およびアンマネージ コードへの呼び出しについて説明します。|

### <a name="deploying-an-application-with-the-appropriate-permissions"></a>適切なアクセス許可を持つアプリケーションの配置

クライアント コンピューターに Windows フォーム アプリケーションを配置する最も一般的な方法は、アプリケーションが実行する必要があるすべてのコンポーネントを記述する配置テクノロジの [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] を使用することです。 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] は、マニフェストと呼ばれる XML ファイルを使用して、アプリケーションを構成するアセンブリとファイル、およびアプリケーションに必要なアクセス許可を記述します。

[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] は、クライアント コンピューターでアクセス許可の昇格を要求するための 2 つのテクノロジを持っています。 どちらのテクノロジも、Authenticode 証明書の使用に依存します。 証明書は、アプリケーションが信頼できる発行元からのものであることをユーザーにある程度保証するのに役立ちます。

次の表では、それらのテクノロジについて説明します。

|昇格されたアクセス許可のテクノロジ|説明|
|------------------------------------|-----------------|
|アクセス許可の昇格|アプリケーションを最初に実行するときにセキュリティ ダイアログ ボックスをユーザーに表示します。 **[アクセス許可の昇格]** ダイアログ ボックスは、アプリケーションの発行者についてユーザーに通知するので、ユーザーは十分な情報に基づいて追加の信頼を付与するかどうかを決定できます。|
|信頼されたアプリケーションの配置|システム管理者がクライアント コンピューターで、発行元の Authenticode 証明書のインストールを 1 回実行する必要があります。 その時点から、その証明書で署名されたアプリケーションは信頼済みとみなされ、追加メッセージを表示せずに、ローカル コンピューター上で完全信頼で実行できます。|

どのテクノロジを選択するかは、配置環境に応じて異なります。 詳細については、「[ClickOnce 配置ストラテジの選択](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy)」を参照してください。

既定では、 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 、Visual Studio を使用してデプロイされたアプリケーションまたは[!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]SDK ツール (Mage.exe および MageUI.exe) が完全信頼を持つクライアント コンピューターで実行するように構成されます。 部分信頼を使用して、またはいくつか追加のアクセス許可のみを使用して、アプリケーションを配置している場合、この既定を変更する必要があります。 Visual Studio でこれを行う、または[!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]SDK ツールの MageUI.exe の配置を構成するときにします。 MageUI.exe を使用する方法の詳細については、チュートリアルを参照してください。コマンドラインから ClickOnce アプリケーションを展開します。  参照してください[方法。ClickOnce アプリケーションのカスタム アクセス許可を設定](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hafybdaa(v=vs.110))または[方法。ClickOnce アプリケーションのカスタム アクセス許可を設定](/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application)します。

[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] とアクセス許可の昇格のセキュリティ面の詳細については、「[ClickOnce アプリケーションのセキュリティ](/visualstudio/deployment/securing-clickonce-applications)」を参照してください。 信頼されたアプリケーションの配置の詳細については、「[信頼されたアプリケーションの配置の概要](/visualstudio/deployment/trusted-application-deployment-overview)」を参照してください。

### <a name="testing-the-application"></a>アプリケーションのテスト

Visual Studio を使用して、Windows フォーム アプリケーションをデプロイする場合は、部分信頼または制限されたアクセス許可のセット、開発環境からでのデバッグを有効にできます。  参照してください[方法。アクセス許可が制限された ClickOnce アプリケーションをデバッグする](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions)」を参照してください。

## <a name="see-also"></a>関連項目

- [Windows フォームのセキュリティ](windows-forms-security.md)
- [コード アクセス セキュリティの基礎](../misc/code-access-security-basics.md)
- [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)
- [信頼されたアプリケーションの配置の概要](/visualstudio/deployment/trusted-application-deployment-overview)
- [Mage.exe (マニフェストの生成および編集ツール)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
