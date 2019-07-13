---
title: UI オートメーションのセキュリティの概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: c74f770f917fc3b2a7d3a18c08270745dac68b12
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422429"
---
# <a name="ui-automation-security-overview"></a>UI オートメーションのセキュリティの概要

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。

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

マニフェスト ファイルが含まれていますが、保護されたシステムの UI にアクセスするアプリケーションを構築する必要があります、`uiAccess`属性、`requestedExecutionLevel`タグを次のようにします。

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

このコードの `level` 属性の値は一例にすぎません。

`uiAccess` 既定では"false"つまり、属性を省略した場合、またはアセンブリのマニフェストが存在しない場合は、アプリケーションできなく保護対象の UI にアクセスします。

詳細については[!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)]セキュリティ、アプリケーションの署名、およびアセンブリのマニフェストを作成する方法を参照してください[開発者のベスト プラクティスと最小限の特権環境でのアプリケーションのガイドライン](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480150(v=msdn.10))します。
