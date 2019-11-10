---
title: Silverlight デバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: b7af03197a43976c47b7ddc30346d622e6b97207
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139146"
---
# <a name="silverlight-debugging"></a>Silverlight デバッグ
このセクションのトピックでは、Windows オペレーティング システム上または Macintosh プラットフォーム上で動作している Silverlight ベースのアプリケーションのデバッグをサポートするために共通言語ランタイム (CLR: Common Language Runtime) で提供される環境とインターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 プロセスで CLR を列挙するメカニズムを提供します。  
  
 [CloseCLREnumeration 関数](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 [列挙型 Ateclrs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)によって返されたハンドルの配列にある有効な CLR 継続スタートアップイベントを閉じ、ハンドルおよび文字列パス配列のメモリを解放します。  
  
 [CreateCoreClrDebugTarget 関数](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。  
  
 [CreateCordbObject 関数](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 リモート プロセスでマネージド デバッグ セッションをインスタンス化するための機能を提供するデバッガー インターフェイスを作成します。  
  
 [CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 対象プロセス内の CLR パスからバージョン文字列を作成します。  
  
 [CreateDebuggingInterfaceFromVersion 関数](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 [Createversionstringfrommodule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)関数から返された CLR バージョン文字列を受け取り、対応するデバッガーインターフェイスを返します。  
  
 [CoreClrDebugProcInfo 構造体](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 リモート コンピューターで実行されているプロセスを表します。  
  
 [CoreClrDebugRuntimeInfo 構造体](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 リモート コンピューター上のプロセスに読み込まれる CLR インスタンスを表します。  
  
 [GetStartupNotificationEvent 関数](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。  
  
 [ICoreClrDebugTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。  
  
 [InitDbgTransportManager 関数](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。  
  
 [ShutdownDbgTransportManager 関数](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 リモート ターゲット コンピューターへの接続のためにトランスポート マネージャーをシャットダウンします。  
  
## <a name="see-also"></a>関連項目

- [デバッグ コクラス](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
