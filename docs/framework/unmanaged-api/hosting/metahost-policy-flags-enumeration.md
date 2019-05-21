---
title: METAHOST_POLICY_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37a6dc0caa81a365727bfc32a6a0363bb7e1713d
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960142"
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS 列挙体
ほとんどのランタイム ホストに共通するバインディング ポリシーを提供します。 この列挙体を使って、 [iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|共通言語ランタイム (CLR) は、現在のプロセスに読み込まれると見なしません高い互換性、ポリシーを定義します。 代わりと見なされるインストールされている Clr のみと、コンポーネントの基本設定、アセンブリ ファイル自体、宣言されたビルド対象のバージョン、または構成ファイルから派生します。|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|完全一致が見つからない場合に、hkey_local_machine \software\microsoft の内容に基づいて、バージョンのバインドの結果にアップグレード ポリシーを適用\\します。NETFramework\Policy\Upgrades します。 これと同じ効果を持つ[RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)します。|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|呼び出しに提供されたイメージは、新しいプロセスで起動された場合に、バインドの結果が返されます。 現時点では、`GetRequestedRuntime`読み込み可能なランタイムのセットを無視し、インストールされているランタイムのセットに対してバインドします。 このフラグは、ホストの起動時に、EXE がバインドするランタイムを決定するを使用します。|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|場合、エラー ダイアログ ボックスが表示される`GetRequestedRuntime`は入力パラメーターと互換性があるランタイムを検索できません。 以降では、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、このエラー ダイアログ ボックスで、適切な機能を有効にする、ユーザーが希望かどうかを確認する Windows 機能 ダイアログ ボックスの形式を取ることができます。|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` バインディング プロセスに追加の入力として、プロセス イメージ (および、対応する構成ファイル) を使用します。 既定では、`GetRequestedRuntime`ことはありません、プロセス イメージのパス (通常は、プロセスを起動するために使用された EXE) にバインドするランタイムを決定するときにします。|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` 情報は、現在の構成ファイルでないときに、適切な SKU がインストールされているかどうかを確認する必要があります。 これにより、アプリケーション、.NET Framework の既定のインストールよりも小さい Sku で適切に失敗する構成ファイルがないことができます。 既定では、 `GetRequestedRuntime` SKU 属性は、構成ファイルで指定されていない場合、適切な SKU がインストールされているかどうかをチェックしません`<supportedRuntime />`要素。|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` SEM_FAILCRITICALERRORS を無視する (呼び出すことによって設定されています、 [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242)関数)、エラー ダイアログ ボックスを表示するとします。 既定では、SEM_FAILCRITICALERRORS は、エラー ダイアログ ボックスを抑制します。 別のプロセスから継承されている可能性があるし、サイレント エラーが実際のシナリオでは望ましくない可能性があります。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Metahost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [GetRequestedRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
