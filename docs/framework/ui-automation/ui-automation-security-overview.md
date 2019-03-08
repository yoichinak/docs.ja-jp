---
title: UI オートメーションのセキュリティの概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 926fed8b2f03e90fd3ccf85564a20ff7b2a7d687
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674381"
---
# <a name="ui-automation-security-overview"></a>UI オートメーションのセキュリティの概要
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 この概要では、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] における [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]のセキュリティ モデルについて説明します。  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>ユーザー アカウント制御  
 セキュリティは [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] の重要点であり、とりわけ顕著な革新として、より高い特権が必要なアプリケーションとサービスの実行を必ずしもブロックされずに、(管理者以外の) 標準ユーザーとして実行する能力が挙げられます。  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]では、ほとんどのアプリケーションに、標準トークンまたは管理トークンのいずれかが付属しています。 アプリケーションが管理アプリケーションとして識別できない場合は、既定で標準のアプリケーションとして起動されます。 管理アプリケーションとして識別されたアプリケーションが起動される前に、 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] は、昇格された権限でアプリケーションを実行することへの同意をユーザーに求めるメッセージを表示します。 ユーザーがローカル管理者グループのメンバーである場合でも、同意を求めるメッセージは既定で表示されます。これは、管理者の資格情報を必要とするアプリケーションまたはシステム コンポーネントが実行の許可を要求するまで、管理者は標準ユーザーとして実行するためです。  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>より高い特権が必要なタスク  
 管理者特権が必要なタスクをユーザーが実行しようとする場合、 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] はユーザーに続行に同意するかを確認するダイアログ ボックスを表示します。 このダイアログ ボックスは、悪意のあるソフトウェアがユーザー入力をシミュレートできないように、プロセス間通信から保護されます。 同様に、デスクトップのログオン画面は、通常は他のプロセスからはアクセスできません。  
  
 UI オートメーション クライアントは、他のプロセスと通信する必要があります。プロセスによっては、より高い特権レベルで実行している可能性があります。 クライアントにも、通常は他のプロセスによって表示できないシステム ダイアログ ボックスへのアクセスが必要になる可能性があります。 そのため、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クライアントはシステムによって信頼されている必要があり、特別な特権で実行する必要があります。  
  
 より高い権限レベルで実行されているアプリケーションと通信する信頼を得るためには、アプリケーションに署名する必要があります。  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>マニフェスト ファイル  
 保護されたシステム [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]にアクセスするためには、マニフェスト ファイル内に特別な属性が含まれるマニフェスト ファイルを使ってアプリケーションをビルドする必要があります。 次のように、この `uiAccess` 属性は `requestedExecutionLevel` タグに含まれます。  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 このコードの `level` 属性の値は一例にすぎません。  
  
 既定では`UIAccess` は "false" です。つまり、属性を省略した場合、またはアセンブリのマニフェストが存在しない場合、アプリケーションは保護された [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]にアクセスできなくなります。  
  
 詳細については[!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)]セキュリティ、アプリケーションの署名、およびアセンブリのマニフェストを作成する方法を参照してください[開発者のベスト プラクティスと最小限の特権環境でのアプリケーションのガイドライン](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480150(v=msdn.10))します。
