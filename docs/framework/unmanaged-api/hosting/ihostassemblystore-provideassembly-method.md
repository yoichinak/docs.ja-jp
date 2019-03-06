---
title: IHostAssemblyStore::ProvideAssembly メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 778664dea16c5183945e25e0261f4a65bb646ac0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467975"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly メソッド
によって参照されているアセンブリへの参照を取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)から返された[ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)します。 共通言語ランタイム (CLR) を呼び出す`ProvideAssembly`一覧に含まれていないアセンブリごとにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pBindInfo`  
 [in]ポインター、 [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)などの任意のバージョン管理ポリシーが存在するか、特定のバインド特性を決定する、ホストが使用するインスタンスにバインドするアセンブリとします。  
  
 `pAssemblyId`  
 [out]これは、要求されたアセンブリの一意の識別子へのポインター`IStream`します。  
  
 `pHostContext`  
 [out]プラットフォームがなくても要求されたアセンブリの証拠を判断するために使用するホスト固有のデータへのポインターは、呼び出しを起動します。 `pHostContext` 対応する、<xref:System.Reflection.Assembly.HostContext%2A>マネージ プロパティ<xref:System.Reflection.Assembly>クラス。  
  
 `ppStmAssemblyImage`  
 [out]アドレスへのポインター、 `IStream` 、読み込まれるまたはアセンブリが見つからなかった場合は null にするポータブル実行可能 (PE) イメージを格納しています。  
  
 `ppStmPDB`  
 [out]アドレスへのポインター、`IStream`を格納しているプログラムのデバッグ (PDB) の情報、または null 場合、.pdb ファイルが見つかりませんでした。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|COR_E_FILENOTFOUND (0x80070002)|要求されたアセンブリを配置できませんでした。|  
|E_NOT_SUFFICIENT_BUFFER|によって指定されたバッファー サイズ`pAssemblyId`ホストを返す必要がある識別子を保持するために十分な大きさではありません。|  
  
## <a name="remarks"></a>Remarks  
 Id 値が返される`pAssemblyId`ホストによって指定されます。 識別子は、プロセスの有効期間内で一意である必要があります。 CLR は、この値をストリームの一意の識別子として使用します。 値に対して各値をチェック`pAssemblyId`するその他の呼び出しによって返される`ProvideAssembly`します。 場合は、ホストは、同じを返します`pAssemblyId`別の値`IStream`CLR は、そのストリームの内容が既にマップされているかどうかを確認します。 そうである場合、ランタイムは、新しいものをマップする代わりに、イメージの既存のコピーを読み込みます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
