---
title: '方法: メッセージング アクティビティを使用してワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: f5bb8df5936be1890bf744300daa7ccb68e341e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787794"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>方法: メッセージング アクティビティを使用してワークフロー サービスを作成する
このトピックでは、メッセージング アクティビティを使用して単純なワークフロー サービスを作成する方法について説明します。 ここでは、メッセージング アクティビティだけで構成されるサービスのワークフロー サービスを作成する機構に重点を置きます。 実際のサービスでは、ワークフローに他の多くのアクティビティが含まれます。 このサービスは、文字列を取得して、それを呼び出し元に返す、Echo という 1 つの操作を実装します。 このトピックは、一連の 2 つのトピックの最初のものです。 次のトピック[How To:サービス アプリケーションからアクセスする、ワークフロー](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)このトピックで作成したサービスを呼び出すことができるワークフロー アプリケーションを作成する方法について説明します。  
  
### <a name="to-create-a-workflow-service-project"></a>ワークフロー サービス プロジェクトを作成するには  
  
1. Visual Studio 2012 を起動します。  
  
2. をクリックして、**ファイル**メニューの [**新規**、し**プロジェクト**を表示する、**新しいプロジェクト] ダイアログ**します。 選択**ワークフロー**インストール済みテンプレートの一覧から、 **WCF ワークフロー サービス アプリケーション**プロジェクトの種類の一覧から。 プロジェクトに名前を`MyWFService`し、次の図に示すように、既定の場所を使用します。  
  
     をクリックして、 **OK**を閉じる、**新しいプロジェクト ダイアログ**します。  
  
3. プロジェクトが作成されると、次の図に示すように、Service1.xamlx ファイルがデザイナーで開かれます。  
  
     ![スクリーン ショットは、デザイナーで、Service1.xamlx ファイルを開くを示しています。](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     というラベルの付いたアクティビティを右クリックして**シーケンシャル サービス**選択**削除**します。  
  
### <a name="to-implement-the-workflow-service"></a>ワークフロー サービスを実装するには  
  
1. 選択、**ツールボックス**をツールボックスを表示し、画鋲のアイコン、ウィンドウを開いたままを画面の左側にあるタブ。 展開、**メッセージング**セクションのツールボックスに次の図に示すように、メッセージング アクティビティおよびメッセージング アクティビティ テンプレートを表示します。  
  
     ![[メッセージング] セクションで、ツールボックスのスクリーン ショットが展開されます。](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. ドラッグ アンド ドロップ、 **ReceiveAndSendReply**をワークフロー デザイナーのテンプレート。 これを作成します、<xref:System.Activities.Statements.Sequence>でアクティビティを**受信**アクティビティの後に、<xref:System.ServiceModel.Activities.SendReply>アクティビティの次の図に示すようにします。  
  
     ![ReceiveAndSendReply テンプレートを示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     <xref:System.ServiceModel.Activities.SendReply> アクティビティの <xref:System.ServiceModel.Activities.SendReply.Request%2A> プロパティは `Receive` に設定されています。これは、<xref:System.ServiceModel.Activities.Receive> アクティビティが応答する <xref:System.ServiceModel.Activities.SendReply> アクティビティの名前です。  
  
3. <xref:System.ServiceModel.Activities.Receive>アクティビティの種類`Echo`というラベルが付いたテキスト ボックスに**OperationName**します。 これにより、サービスが実装する操作の名前が定義されます。  
  
     ![操作名を指定する場所を示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. <xref:System.ServiceModel.Activities.Receive>をクリックしてまだ開いていない場合は、選択すると、アクティビティにより、プロパティ ウィンドウを開き、**ビュー**メニュー**プロパティ ウィンドウ**します。 **プロパティ ウィンドウ**が表示されるまで下にスクロール**CanCreateInstance**次の図に示すように、チェック ボックスをクリックします。 この設定によって、ワークフロー サービス ホストはメッセージが受信されると (必要に応じて) サービスの新しいインスタンスを作成できるようになります。  
  
     ![CanCreateInstance プロパティを示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. 選択、<xref:System.Activities.Statements.Sequence>アクティビティをクリックして、**変数**デザイナーの左下隅のボタンをクリックします。 これにより、変数エディターが開かれます。 をクリックして、**変数の作成**のリンクを操作に送信される文字列を格納する変数を追加します。 変数の名前`msg`設定とその**変数**次の図に示すように、文字列を入力します。  
  
     ![変数を追加する方法を示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     をクリックして、**変数**ボタンをもう一度、変数エディターを閉じます。  
  
6. をクリックして、**定義.** 内のリンク、**コンテンツ**テキスト ボックスに、<xref:System.ServiceModel.Activities.Receive>を表示するアクティビティ、**コンテンツ定義**ダイアログ。 選択、**パラメーター**ラジオ ボタンをクリックして、**新しいパラメーターを追加**リンクに、入力`inMsg`で、**名前**テキスト ボックスで、**文字列**で、**型**ドロップダウン リスト ボックス、および種類`msg`で、**を割り当てる**テキスト ボックスの次の図に示すようにします。  
  
     ![コンテンツのパラメーターを追加することを示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     これにより、Receive アクティビティが文字列パラメーターを受け取り、そのデータが `msg` 変数にバインドされるように指定されます。 をクリックして**OK**を閉じる、**コンテンツ定義**ダイアログ。  
  
7. をクリックして、**を定義しています.** のリンクを**コンテンツ**ボックスに、<xref:System.ServiceModel.Activities.SendReply>を表示するアクティビティ、**コンテンツ定義**ダイアログ。 選択、**パラメーター**ラジオ ボタンをクリックして、**新しいパラメーターを追加**リンクに、入力`outMsg`で、**名前** ボックスに、選択**文字列**で、**型**ドロップダウン リスト ボックス、および`msg`で、**値**テキスト ボックスの次の図に示すようにします。  
  
     ![OutMsg パラメーターを追加する方法を示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     これにより、<xref:System.ServiceModel.Activities.SendReply> アクティビティがメッセージまたはメッセージ コントラクト型を送信し、そのデータが `msg` 変数にバインドされるように指定されます。 これは <xref:System.ServiceModel.Activities.SendReply> アクティビティであるため、`msg` のデータは、アクティビティがクライアントに送り返すメッセージの設定に使用されます。 をクリックして**OK**を閉じる、**コンテンツ定義**ダイアログ。  
  
8. 保存しをクリックして、ソリューションをビルド、**ビルド**メニュー**ソリューションのビルド**します。  
  
## <a name="configure-the-workflow-service-project"></a>ワークフロー サービス プロジェクトの構成  
 ワークフロー サービスは完成しました。 ここでは、ホストと実行を容易にするように、ワークフロー サービス ソリューションを構成する方法について説明します。 このソリューションでは、ASP.NET 開発サーバーを使用してサービスをホストします。  
  
#### <a name="to-set-project-start-up-options"></a>プロジェクトのスタートアップ オプションを設定するには  
  
1. **ソリューション エクスプ ローラー**、右クリック**MyWFService**選択と**プロパティ**を表示する、**プロジェクトのプロパティ**ダイアログ。  
  
2. 選択、 **Web**タブおよび選択**特定のページ****開始動作**と種類`Service1.xamlx`次の図に示すように、テキスト ボックスに。  
  
     ![プロジェクトの [プロパティ] ダイアログ ボックスのスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     これにより、ASP.NET 開発サーバーの Service1.xamlx で定義されたサービスがホストされます。  
  
3. Ctrl キーを押しながら F5 キーを押して、サービスを起動します。 次の図に示すように、ASP.NET 開発サーバーのアイコンが、デスクトップの右下側に表示されます。  
  
     ![ASP.NET 開発サーバーのアイコンを示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     また、Internet Explorer に、サービスの WCF サービス ヘルプ ページが表示されます。  
  
     ![WCF サービス ヘルプ ページを示すスクリーン ショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. 進み、[方法。サービス アプリケーションからアクセスする、ワークフロー](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)をこのサービスを呼び出すワークフロー クライアントを作成するトピック。  
  
## <a name="see-also"></a>関連項目

- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [ワークフロー サービスのホストの概要](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [メッセージング アクティビティ](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
