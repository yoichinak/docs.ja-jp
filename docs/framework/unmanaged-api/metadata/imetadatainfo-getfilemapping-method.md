---
title: IMetaDataInfo::GetFileMapping メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175266"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping メソッド
マップされたファイルのメモリ領域とマッピングの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppvData`  
 [アウト]マップされたファイルの先頭へのポインター。  
  
 `pcbData`  
 [アウト]マップされた領域のサイズ。 の`pdwMappingType``fmFlat`場合、これはファイルのサイズです。  
  
 `pdwMappingType`  
 [アウト]マッピングの種類を示す[CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)値。 共通言語ランタイム (CLR) の現在の実装は常`fmFlat`にを返します。 他の値は将来使用するために予約されています。 ただし、その他の値は将来のバージョンまたはサービス リリースで有効になる可能性があるため、戻り値は常に確認する必要があります。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|すべての出力が入力されます。|  
|`E_INVALIDARG`|NULL が引数値として渡されました。|  
|`COR_E_NOTSUPPORTED`|CLR の実装では、メモリ領域に関する情報を提供できません。 これが発生する理由としては次のようなことが考えられます。<br /><br /> - メタデータ スコープがまたは`ofWrite``ofCopyMemory`フラグ付きで開かれました。<br />- メタデータ スコープは`ofReadOnly`フラグなしで開かれました。<br />-[ファイル](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)のメタデータ部分のみを開くためにメソッドを使用しました。<br />- ファイルはポータブル実行可能 (PE) ファイルではありません。 **注:** これらの条件は CLR の実装に依存し、CLR の将来のバージョンでは弱くなる可能性があります。|  
  
## <a name="remarks"></a>解説  
 参照する`ppvData`メモリは、基になるメタデータ スコープが開いている場合にのみ有効です。  
  
 このメソッドを動作させるには[、IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)メソッドを呼び出してディスク上のファイルのメタデータをメモリにマップする場合は、`ofReadOnly`フラグを指定する必要があり、または`ofWrite``ofCopyMemory`フラグを指定しないでください。  
  
 各スコープのファイル マッピングの種類は、特定の CLR の実装に固有です。 ユーザーが設定することはできません。 CLR の現在の実装は常`fmFlat`に`pdwMappingType`に戻りますが、これは CLR の将来のバージョンや特定のバージョンの将来のサービス リリースで変更される可能性があります。 では、異なる型のレイアウトと`pdwMappingType`オフセットが異なるため、常に戻り値をチェックする必要があります。  
  
 3 つのパラメーターのいずれに対しても NULL を渡すことはサポートされていません。 メソッドは`E_INVALIDARG`を返し、出力は何も入力されません。 マッピング・タイプまたは領域のサイズを無視すると、プログラムが異常終了する可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataInfo インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping 列挙体](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
