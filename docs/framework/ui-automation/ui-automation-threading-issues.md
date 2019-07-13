---
title: UI オートメーション スレッド処理の問題点
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 83b8ec67cff7006e736e0f65a7339b340b20d458
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678593"
---
# <a name="ui-automation-threading-issues"></a>UI オートメーション スレッド処理の問題点
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] の Windows メッセージを使用する方法が原因で、クライアント アプリケーションが [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] スレッド上のそれ自体の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] と対話しようとするときに、競合が発生する可能性があります。 これらの競合が発生すると、パフォーマンスが著しく低下する恐れがあります。また、アプリケーションが応答を停止する可能性もあります。  
  
 クライアント アプリケーションがデスクトップ上のすべての要素 (それ自体の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]を含む) と対話する場合、すべての [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の呼び出しを個別のスレッドで実行する必要があります。 これには、要素の検索 (たとえば、 <xref:System.Windows.Automation.TreeWalker> または <xref:System.Windows.Automation.AutomationElement.FindAll%2A> メソッドを使用) とコントロール パターンの使用が含まれます。  
  
 イベント ハンドラーは常に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 以外のスレッドで呼び出されるため、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の呼び出しを[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] イベント ハンドラー内で実行しても問題ありません。 ただし、クライアント アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]から発生するイベントをサブスクライブする場合、 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>以外のスレッド上の[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (または関連するメソッド) への呼び出しを実行する必要があります。 同じスレッドにあるイベント ハンドラーを削除します。
