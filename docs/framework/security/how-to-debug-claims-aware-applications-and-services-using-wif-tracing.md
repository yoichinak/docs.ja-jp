---
title: '方法: WIF トレースを使用してクレーム対応アプリケーションおよびサービスをデバッグする'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: effd670a4d0e12f0bca10301fabc361c73e03328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625878"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>方法: WIF トレースを使用してクレーム対応アプリケーションおよびサービスをデバッグする
## <a name="applies-to"></a>対象  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- サービス トレース ビューアー ツール (SvcTraceViewer.exe)  
  
- WIF アプリケーションのトラブルシューティングとデバッグ  
  
## <a name="summary"></a>まとめ  
 この方法では、WIF トレースの構成方法、トレース ログの収集方法、およびトレース ビューアー ツールを使用してトレース ログを分析する方法について、必要な手順を説明します。 WIF に関連する問題をトラブルシューティングするために、必要なアクションに対してトレース エントリの全般的なマッピングを行います。  
  
## <a name="contents"></a>目次  
  
- 目的  
  
- 手順の要約  
  
- 手順 1 – Web.config 構成ファイルを使用して WIF のトレースを構成する  
  
- 手順 2 – トレース ビューアー ツールを使用して WIF のトレース ファイルを分析する  
  
- 手順 3 – WIF 関連の問題を修復するための解決策を特定する  
  
- 関連項目  
  
## <a name="objectives"></a>目的  
  
- WIF トレースを構成する。  
  
- トレース ビューアー ツールでトレース ログを表示する。  
  
- トレース ログで WIF 関連の問題を特定する。  
  
- トレース ログで検出された WIF 関連の問題に修正措置を適用する。  
  
## <a name="summary-of-steps"></a>手順の要約  
  
- 手順 1 – Web.config 構成ファイルを使用して WIF のトレースを構成する  
  
- 手順 2 – トレース ビューアー ツールを使用して WIF のトレース ファイルを分析する  
  
- 手順 3 – WIF 関連の問題を修復するための解決策を特定する  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>手順 1 – Web.config 構成ファイルを使用して WIF のトレースを構成する  
 この手順では、*Web.config* ファイルの構成セクションに変更を加えて、WIF がイベントをトレースしてトレース ログに格納できるようにします。  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Web.config 構成ファイルを使用して WIF のトレースを構成するには  
  
1. **ソリューション エクスプローラー**で、Visual Studio エディターのルートの **Web.config** または **App.config** 構成ファイルをダブルクリックして開きます。 ソリューションに **Web.config** または **App.config** 構成ファイルがない場合は、**ソリューション エクスプローラー**でソリューションを右クリックし、**[追加]**、**[新しい項目...]** の順にクリックして追加します。 **[新しい項目]** ダイアログ ボックスで、リストから **[アプリケーション構成ファイル]** (**App.config** の場合) または **[Web 構成ファイル]** (**Web.config** の場合) を選択して、**[OK]** をクリックします。  
  
2. 構成ファイルの最後にある **\<configuration>** ノード内に、以下のような構成エントリを追加します。  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3. 上記の構成は、詳細トレース イベントを生成し、*WIFTrace.e2e* ファイルにログを記録するよう WIF に指示します。 値の完全な一覧については、 **switchValue**スイッチ、次のトピックで、トレース レベルの表を参照してください。[トレースの構成](../wcf/diagnostics/tracing/configuring-tracing.md)します。  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>手順 2 – トレース ビューアー ツールを使用して WIF のトレース ファイルを分析する  
 このステップでは、トレース ビューアー ツール (SvcTraceViewer.exe) を使用して WIF のトレース ログを分析します。  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>トレース ビューアー ツール (SvcTraceViewer.exe) を使用して WIF のトレース ログを分析するには  
  
1. トレース ビューアー ツール (SvcTraceViewer.exe) は、Windows SDK の一部として同梱されています。 既に Windows SDK をインストールしていない場合は、ここでダウンロードできます。[Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279)します。  
  
2. トレース ビューアー ツール (SvcTraceViewer.exe) を実行します。 通常、これはインストール パスの **Bin** フォルダーから使用できます。  
  
3. たとえば、WIF トレースのログ ファイル WIFTrace.e2e を開きます。その場合、メニューで **[ファイル]**、**[開く...]**  オプションの順に選択するか、**Ctrl + O** ショートカット キーを使用します。 トレース ビューアー ツールでトレース ログ ファイルが開きます。  
  
4. **[アクティビティ]** タブでエントリを確認します。各エントリには、アクティビティの数、ログに記録されたトレースの数、アクティビティの期間および開始と終了のタイムスタンプが含まれているはずです。  
  
5. **[アクティビティ]** タブをクリックします。ツールのメイン領域に詳細なトレース エントリが表示されます。 使用して、**レベル**ドロップダウン リストで、メニューなどの特定のレベルのトレースをフィルター処理には。**すべて**、**警告**、**エラー**、**情報**など。  
  
6. 特定のトレース エントリをクリックすると、ツールの下部の領域で詳細をレビューできます。 詳細は、対応するタブを選択することで、**書式付き**および **XML** ビューで表示することができます。  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>手順 3 – WIF 関連の問題を修復するための解決策を特定する  
 この手順では、WIF のトレース ログとトレース ビューアー ツールを使用して、WIF に関連する問題の解決方法を特定できます。 WIF 関連の例外と、問題をトラブルシューティングするための可能性のある解決策や必要な操作との全般的なマッピングを概説しています。  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>WIF 関連の問題を修復するための解決策を特定するには  
  
1. WIF の例外と問題を修正するために必要な操作に関する次の表を確認します。  
  
|**エラー ID**|**エラー メッセージ**|**エラーを修復するために必要な操作**|  
|-|-|-|  
|ID4175|セキュリティ トークンの発行者は、IssuerNameRegistry で認識されませんでした。  この発行者からのセキュリティ トークンを承認するには、この発行者の有効な名前を返すように IssuerNameRegistry を構成します。|このエラーは、MMC スナップインから拇印をコピーして、*Web.config* ファイルに貼り付けると発生する可能性があります。 具体的には、[証明書のプロパティ] ウィンドウからコピーするときに、テキスト文字列内で余分な印刷できない文字を取得することがあります。 この余分な文字により、拇印と失敗しますを。正しく拇印をコピーする手順をご覧[クレーム ベースのシングル サインオン-で、Web アプリケーションおよび Microsoft Azure 用](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29)します。|  
  
## <a name="related-items"></a>関連項目  
  
- [サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
