---
title: .NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96bc833915dd74756220b5e79a2866b41389dd45
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630504"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス
このセクションがアンマネージ インターフェイスについて説明しますホストを使用して、共通言語ランタイム (CLR) 統合、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、以降のバージョンをアプリケーションにします。 これらのインターフェイスは、ホストを構成し、ランタイムをプロセスに読み込むのためのメソッドを提供します。  
  
 以降では、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、すべてのホスティング インターフェイスで次の特性があります。  
  
- 有効期間管理を使用して、(`AddRef`と`Release`)、(暗黙のコンテキスト) をカプセル化し、 `QueryInterface` COM から  
  
- ある型を使用しないで COM など`BSTR`、 `SAFEARRAY`、または`VARIANT`します。  
  
- アパートメント モデル、集計、またはレジストリのアクティブ化を使用するがない、 [CoCreateInstance 関数](https://go.microsoft.com/fwlink/?LinkId=142894)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ICLRAppDomainResourceMonitor インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 アプリケーション ドメインのメモリと CPU 使用率を確認するメソッドを提供します。  
  
 [ICLRDomainManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 初期化プロパティを指定して、既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーを指定するホストを有効にします。  
  
 [ICLRGCManager2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 提供、 [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)メソッドで、ホストがガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズの値より大きいに設定できるように`DWORD`します。  
  
 [ICLRMetaHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 CLR の特定のバージョンを返す、インストールされている Clr のすべてを一覧表示、すべてのプロセス内ランタイムを一覧表示、アクティブ化のインターフェイスを返す、アセンブリをコンパイルするために使用する CLR のバージョンを検出するメソッドを提供します。  
  
 [ICLRMetaHostPolicy インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 提供、 [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) CLR インターフェイスを提供する方法、ポリシーの条件、マネージ アセンブリ、バージョン、および構成ファイルに基づいています。  
  
 [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 バージョン、ディレクトリ、および負荷の状態を含む、特定のランタイムに関する情報を返すメソッドを提供します。  
  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 厳密な名前を持つアセンブリに署名するための基本的なグローバル静的関数を提供します。 すべての[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)メソッドは、標準の COM Hresult を返します。  
  
 [ICLRStrongName2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Sha-2 (sha-256、sha-384、および sha-512) のハッシュ アルゴリズムをセキュリティで保護グループを使用する厳密な名前を作成する機能を提供します。  
  
 [ICLRTask2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 すべての機能を提供、 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)。 さらに、現在のスレッドが遅延するスレッドの中止を許可するメソッドを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [非推奨の CLR のホスト インターフェイスおよびコクラス](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework version 1.0 および 1.1 で提供されるホスティング インターフェイスをについて説明します。  
  
 [CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 .NET Framework バージョン 2.0、3.0、および 3.5 で提供されるホスティング インターフェイスについて説明します。  
  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 .NET Framework でのホスティングについて説明します。
