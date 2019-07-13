---
title: STARTUP_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f254582d96b310c247778818fc0d5daaae0d911c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737265"
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS 列挙型
共通言語ランタイム (CLR: Common Language Runtime) の起動動作を示す値を含みます。 既定では、ガベージ コレクションは非同時実行で、基底クラス ライブラリだけがドメイン中立領域に読み込まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|同時実行ガベージ コレクションを使用することを指定します。 呼び出し元がサーバー ビルドと同時実行ガベージ コレクションをシングル プロセッサ コンピューター上で要求した場合は、代わりにワークステーション ビルドと非同時実行ガベージ コレクションが実行されます。 **注:** 同時実行ガベージ コレクションは、Intel Itanium アーキテクチャ (以前の IA-64) を実装する 64 ビット システム上で WOW64 x86 エミュレーターを実行しているアプリケーションではサポートされません。 64 ビット Windows システム上で WOW64 の使用に関する詳細については、次を参照してください。[を実行している 32 ビット アプリケーション](/windows/desktop/WinProg64/running-32-bit-applications)します。|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|ローダーの最適化を行う必要があることを指定します。|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|どのアセンブリもドメイン中立として読み込まないことを指定します。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|すべてのアセンブリをドメイン中立として読み込むことを指定します。|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|厳密な名前を付けられたすべてのアセンブリをドメイン中立として読み込むことを指定します。|  
|`STARTUP_LOADER_SAFEMODE`|CLR バージョン ポリシーが、渡されたバージョンに適用されないことを指定します。 指定された CLR のバージョンが読み込まれます。 シムは、互換性のある最新バージョンを決めるためのポリシーの評価を実行しません。|  
|`STARTUP_LOADER_SETPREFERENCE`|推奨ランタイムを設定するように指定しますが、実際には起動されません。|  
|`STARTUP_SERVER_GC`|サーバー ガベージ コレクションを使用することを指定します。|  
|`STARTUP_HOARD_GC_VM`|ガベージ コレクションで、使用された仮想アドレスを保持することを指定します。|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|ホスト インターフェイスの混合を許可しないことを指定します。|  
|`STARTUP_LEGACY_IMPERSONATION`|既定として偽装が非同期ポイント間をフローしないように指定します。|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|スレッドが実行を開始するときにスレッド スタック全体をコミットしないことを指定します。|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|マネージド偽装およびプラットフォーム呼び出しによって実行された偽装が非同期ポイント間をフローするように指定します。 既定では、マネージド偽装だけが非同期ポイント間をフローします。|  
|`STARTUP_TRIM_GC_COMMIT`|システム メモリが少ないときに、ガベージ コレクションによるコミットされた領域の使用量を抑えることを指定します。 参照してください`gcTrimCommitOnLowMemory`で[共有 Web ホストの最適化](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)します。|  
|`STARTUP_ETW`|共通言語ランタイム イベントで Windows イベント トレーシング (ETW) が有効になっていることを指定します。 Windows Vista 以降、イベントのトレースは常に有効、ため、このフラグは影響を与えません。 参照してください[.NET Framework のログ記録を制御する](../../../../docs/framework/performance/controlling-logging.md)します。|  
|`STARTUP_ARM`|アプリケーション ドメインのリソース監視が有効になっていることを指定します。 参照してください、<xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>プロパティと[ \<appDomainResourceMonitoring > 要素](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
