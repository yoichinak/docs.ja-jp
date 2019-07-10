---
title: IHostAssemblyStore::ProvideModule メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9290fd70b17b5a6456d85cb4b037ebbc62e028f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763979"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule メソッド
アセンブリまたは、リンクされた (ただし、埋め込まれたされません) 内のモジュールのリソース ファイルを解決します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pBindInfo`  
 [in]ポインターを[ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) 、要求されたモジュールを記述するインスタンス<xref:System.AppDomain>アセンブリとモジュール名。  
  
 `pdwModuleId`  
 [out]一意の識別子へのポインター、`IStream`読み込まれたモジュールを格納しています。  
  
 `ppStmModuleImage`  
 [out]アドレスへのポインター、`IStream`を読み込む、ポータブル実行可能 (PE) イメージを含むオブジェクト。 または、モジュールが見つからなかった場合は null です。  
  
 `ppStmPDB`  
 [out]アドレスへのポインター、 `IStream` 、要求されたモジュールのプログラムのデバッグ (PDB) の情報が含まれるオブジェクト。 または、.pdb ファイルが見つかりませんでした場合は null です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ProvideModule` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|COR_E_FILENOTFOUND (0x80070002)|要求されたアセンブリまたはリンクされたリソースを配置できませんでした。|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` ホストを返す必要がある識別子を格納するのに十分な大きさがありません。|  
  
## <a name="remarks"></a>Remarks  
 Id 値が返される`pdwModuleId`ホストによって指定されます。 識別子は、プロセスの有効期間内で一意である必要があります。 CLR では、関連付けられているストリームの一意識別子としてこの値を使用します。 値に対して各値をチェック`pAssemblyId`への呼び出しによって返される[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)の値に対して、`pdwModuleId`するその他の呼び出しによって返される`ProvideModule`します。 別のホストが同じ識別子の値を返す場合`IStream`CLR は、そのストリームの内容が既にマップされているかどうかを確認します。 そうである場合、CLR は、新しいものをマップする代わりに、イメージの既存のコピーを読み込みます。 そのため、識別子も重複してはなりませんから返されたアセンブリ識別子を持つ`ProvideAssembly`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
