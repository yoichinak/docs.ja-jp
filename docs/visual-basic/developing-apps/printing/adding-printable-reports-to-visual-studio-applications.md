---
title: Visual Studio アプリケーションへの印刷可能なレポートの追加
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 65264deea3aeff1a633ea6888b3f175031b7fba5
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212015"
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Visual Studio アプリケーションへの印刷可能なレポートの追加
Visual Studio では、さまざまな豊富なデータを Visual Basic アプリケーションにレポートを追加するためのレポート ソリューションをサポートしています。 作成し、ReportViewer コントロール、Crystal Reports、または SQL Server Reporting Services を使用してレポートを追加できます。  

  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Visual Basic アプリケーションで Microsoft レポート テクノロジの概要  
 Microsoft レポート アプリケーションでのテクノロジを使用する、次の方法から選択します。  
  
-   Visual Basic Windows アプリケーションに ReportViewer コントロールの 1 つまたは複数のインスタンスを追加します。  
  
-   レポート サーバー Web サービスを呼び出してプログラムで SQL Server Reporting Services を統合します。  
  
-   使用して、ReportViewer コントロールと Microsoft SQL Server 2005 Reporting Services、レポート ビューアーとレポート サーバーとしてコントロールを使用すると、レポート プロセッサ。 (レポート サーバーと、ReportViewer コントロールを一緒に使用する場合は、SQL Server 2005 バージョンの Reporting Services を使用する必要がありますに注意してください。)  
  
## <a name="using-reportviewer-controls"></a>ReportViewer コントロールを使用します。  
 Visual Basic Windows アプリケーションにレポート機能を埋め込むの最も簡単な方法では、アプリケーションでフォームに ReportViewer コントロールを追加します。 コントロールは、レポート処理機能をアプリケーションに直接を追加し、任意の ADO.NET データ オブジェクトからデータを使用してレポートを作成できるように、統合レポート デザイナーを提供します。 フル機能の API は、コントロールへのプログラムによるアクセスを提供し、実行時の機能を構成するようにを報告します。  
  
 ReportViewer は、組み込みのレポート処理と自由に配布可能な 1 つのデータ コントロールでの機能の表示を提供します。 次のレポート機能が必要な場合、レポート ビューアー コントロールを選択します。  
  
-   レポートは、クライアント アプリケーションで処理します。 コントロールによって提供される、表示領域に、処理されたレポートが表示されます。  
  
-   ADO.NET データ テーブルにデータ バインディング。 使用するレポートを作成することができます<xref:System.Data.DataTable>コントロールに指定されたインスタンス。 ビジネス オブジェクトに直接バインドすることもできます。  
  
-   アプリケーションに含めることができる再頒布可能パッケージを制御します。  
  
-   ページ ナビゲーション、印刷、検索、およびエクスポート形式などのランタイム機能。 ReportViewer ツールバーでは、これらの操作をサポートします。  
  
 ReportViewer コントロールを使用することからドラッグできます、**データ**Visual Basic Windows アプリケーションでフォームに、Visual Studio ツールボックスのセクション。  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>Visual Studio でのレポートを ReportViewer コントロールの作成  
 ReportViewer で実行されているレポートを作成するには追加、**レポート**プロジェクト テンプレート。 Visual Studio は、クライアント レポート定義 (.rdlc) ファイルを作成、ファイルをプロジェクトに追加および Visual Studio ワークスペースで、統合レポート デザイナーを開きます。  
  
 Visual Studio レポート デザイナーの統合、**データソース**ウィンドウ。 フィールドをドラッグすると、**データソース**レポート、レポート デザイナーにウィンドウが、レポート定義ファイルにデータ ソースに関するメタデータをコピーします。 このメタデータは、データ バインド コードを自動的に生成する ReportViewer コントロールによって使用されます。  
  
 Visual Studio レポート デザイナーでは、レポートのプレビュー機能は含まれません。 レポートをプレビューするには、アプリケーションを実行し、そこに埋め込まれたレポートをプレビューします。  
  
|基本的なレポート機能をアプリケーションに追加するには|  
|---|    
|1.ReportViewer コントロールをドラッグして、**データ**のタブ、**ツールボックス**フォームにします。<br />2.**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 **新しい項目の追加**ダイアログ ボックスで、**レポート**アイコンをクリックします**追加**します。<br />     レポート デザイナーが、開発環境で開いたし、レポート (.rdlc) ファイルがプロジェクトに追加します。<br />3.レポート アイテムをドラッグ、**ツールボックス**レポート レイアウト上とするように配置します。<br />4.フィールドをドラッグ、**データソース**レポート レイアウトのレポート アイテムにウィンドウ。|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Visual Basic アプリケーションでの Reporting Services を使用します。  
 Reporting Services は、サーバー ベースのレポート テクノロジで、SQL Server に含まれています。 Reporting Services には、ReportViewer コントロールではない追加機能が含まれています。 次の機能のいずれかが必要な場合は、Reporting Services を選択します。  
  
-   スケール アウト配置とサーバー側のレポート処理と大量のレポートの利用状況の複雑なまたは実行時間の長いレポートのパフォーマンスの向上を提供します。  
  
-   形式を出力するは、統合データとレポートの処理、カスタム レポート コントロールとリッチなレンダリングをサポート。  
  
-   レポートの実行時に正確に指定できるようにレポートの処理をスケジュールします。  
  
-   サブスクライバー ベースのレポートの配布を電子メールまたはファイル共有の場所にします。  
  
-   アドホック レポートの必要に応じて、ビジネス ユーザーがレポートを作成できるようにします。  
  
-   動的な受信者一覧にカスタマイズされたレポート出力をルーティングするデータ ドリブン サブスクリプション。  
  
-   データ処理、レポートの配信、カスタム認証、およびレポートの表示用のカスタム拡張機能。  
  
 レポート サーバーは、Web サービスとして実装されます。 アプリケーション コードでは、レポートおよびその他のメタデータにアクセスする Web サービスへの呼び出しを含める必要があります。 Web サービスは、レポート サーバー インスタンスに完全にプログラムによるアクセスを提供します。  
  
 Reporting Services は、Web ベースのレポート テクノロジであるために、既定のビューアーは、HTML 形式で表示されるレポートを示します。 既定のレポートの表示形式として HTML を使用しない場合は、アプリケーションのカスタム レポート ビューアーを記述する必要があります。  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Visual Studio でのレポートを Reporting Services の作成  
 レポート サーバー上で実行されるレポートを作成するには、作成するレポート定義 (.rdl) ファイル、Business Intelligence Development Studio で Visual Studio で SQL Server 2005 に含まれています。  
  
 Business Intelligence Development Studio は、SQL Server コンポーネントに固有のプロジェクト テンプレートを追加します。 レポートを作成するにはから選択することができます、**レポート サーバー プロジェクト**または**レポート サーバー プロジェクト ウィザード**テンプレート。 データ ソースの接続とデータ ソースの種類、SQL Server、Oracle、Analysis Services、XML、SQL Server Integration Services などのさまざまなクエリを指定することができます。 A**データ** タブで、**レイアウト** タブと**プレビュー**  タブでは、データ定義をレポートのレイアウトを作成し、すべて、同じワークスペースでレポートをプレビューすることができます。  
  
 コントロールまたはレポート サーバー用に作成するレポート定義は、どちらのテクノロジで再利用できます。  
  
|レポート サーバーで実行されているレポートを作成するには|  
|---|    
|1.**ファイル**] メニューの [選択**新規**します。<br />     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。<br />2.**プロジェクトの種類**ウィンドウで、をクリックして**ビジネス インテリジェンス プロジェクト**します。<br />3.[テンプレート] ペインで選択**レポート サーバー プロジェクト**または**レポート サーバー プロジェクト ウィザード**します。|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>ReportViewer コントロールと SQL Server Reporting Services を一緒に使用します。  
 SQL Server 2005 Reporting Services、ReportViewer コントロールは、同じアプリケーション内でまとめて使用できます。  
  
-   ReportViewer コントロールは、アプリケーションでレポートを表示するために使用するビューアーを提供します。  
  
-   Reporting Services レポートを提供し、リモート サーバーのすべての処理を実行します。  
  
 Reporting Services レポート サーバーをリモートで格納され処理されるレポートを表示するのには、ReportViewer コントロールを構成できます。 この種類の構成と呼びます*リモート処理モード*します。 リモート処理モードでは、コントロールは、リモートのレポート サーバーに格納されているレポートを要求します。 レポート サーバーでは、すべてのレポートの処理、データ処理、およびレポートの表示を実行します。 完成した、レンダリングされたレポートがコントロールに返され、表示領域に表示されます。  
  
 その他のレポート サーバーのサポートで実行されるレポート形式のエクスポート、別のレポート パラメーター化の実装があるでロールベースの承認モデルを介してアクセス、レポート サーバーによってサポートされているデータ ソースの種類を使用して、レポート サーバー。  
  
 リモート処理モードを使用するには、ReportViewer コントロールを構成するときに、URL とサーバーのレポートへのパスを指定します。
