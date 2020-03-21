---
title: IMetaDataEmit::DefineMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177675"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod メソッド
指定したシグネチャを持つメソッドまたはグローバル関数の定義を作成し、そのメソッド定義にトークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]メソッド`mdTypedef`の親クラスまたは親インターフェイスのトークン。 グローバル`td`関数`mdTokenNil`を定義する場合は、 に設定します。  
  
 `szName`  
 [in]ユニコードのメンバー名。  
  
 `dwMethodFlags`  
 [in]メソッドまたはグローバル関数の属性を指定する[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙体の値。  
  
 `pvSigBlob`  
 [in]メソッド シグネチャ。 署名は、指定されたとおりに永続化されます。 パラメーターに追加情報を指定する必要がある場合は、[メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)を使用します。  
  
 `cbSigBlob`  
 [in]のバイト数`pvSigBlob`。  
  
 `ulCodeRVA`  
 [in]コードのアドレス。  
  
 `dwImplFlags`  
 [in]メソッドの実装機能を指定する[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列挙の値。  
  
 `pmd`  
 [アウト]メンバー トークン。  
  
## <a name="remarks"></a>解説  
 メタデータ API は、メソッドを、パラメーターで指定されている特定の外側のクラスまたはインターフェイスに対して呼び出し元が出力する順序と`td`同じ順序で永続化します。  
  
 使用および特定のパラメータ設定`DefineMethod`に関する追加情報は以下に示します。  
  
## <a name="slots-in-the-v-table"></a>V テーブル内のスロット  
 ランタイムはメソッド定義を使用して v テーブル スロットを設定します。 COM インターフェイス レイアウトとのパリティを保持するなど、1 つ以上のスロットをスキップする必要がある場合は、v テーブル内のスロットまたはスロットを取り込むダミー メソッドが定義されます。`dwMethodFlags``mdRTSpecialName`[を、CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙体の値に設定し、名前を次のように指定します。  
  
 _VtblGap\<*シーケンス*>\<番号\_*カウントの数*>
  
 シーケンス*番号*はメソッドのシーケンス番号で *、CountOfSlots*は v テーブルでスキップするスロットの数です。 *CountOfSlots を*省略すると、1 が想定されます。 これらのダミー メソッドは、マネージ コードまたはアンマネージ コードから呼び出す可能性があり、マネージ コードまたはアンマネージ コードから呼び出そうとすると例外が生成されます。 その唯一の目的は、ランタイムが COM 統合用に生成する v テーブル内の領域を取り込むためです。  
  
## <a name="duplicate-methods"></a>メソッドの重複  
 重複するメソッドを定義しないでください。 つまり`DefineMethod`、 `td`、および`wzName``pvSig`パラメーターの値の重複したセットを呼び出す必要はありません。 (これらの 3 つのパラメーターを一緒にメソッドを一意に定義します。 ただし、メソッド定義の 1 つに対して、パラメーターにビットを`mdPrivateScope`設定する場合は、重複するトリプル`dwMethodFlags`を使用できます。 (ビット`mdPrivateScope`は、コンパイラがこのメソッド定義への参照を出力しないことを意味します。  
  
## <a name="method-implementation-information"></a>メソッド実装情報  
 メソッドの実装に関する情報は、メソッドが宣言された時点では不明な場合があります。 したがって、 を呼び出すときに、`ulCodeRVA`パラメータ`dwImplFlags`に値を`DefineMethod`渡す必要はありません。 値は、必要に応じて[後で IMetaDataEmit:::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)または[IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)を介して指定できます。  
  
 プラットフォーム呼び出し (PInvoke) や COM 相互運用シナリオなど、状況によっては、メソッド本体は提供されず`ulCodeRVA`、0 に設定する必要があります。 このような場合、ランタイムは実装を検索するため、メソッドを抽象としてタグ付けしないでください。  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke のメソッドの定義  
 PInvoke を通じて呼び出されるアンマネージ関数ごとに、ターゲットアンマネージ関数を表すマネージ メソッドを定義する必要があります。 マネージ メソッドを定義するには、PInvoke の使用方法に応じて、いくつかのパラメーターを特定の値に設定して使用`DefineMethod`します。  
  
- True PInvoke - アンマネージ DLL に存在する外部アンマネージ メソッドの呼び出しを伴います。  
  
- ローカル PInvoke - 現在のマネージ モジュールに埋め込まれているネイティブアンマネージ メソッドの呼び出しを含みます。  
  
 パラメータの設定は次の表のとおりです。  
  
|パラメーター|真の PInvoke の値|ローカル PInvoke の値|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||設定`mdStatic`;クリア`mdSynchronized`および`mdAbstract`.|  
|`pvSigBlob`|有効なマネージ型のパラメーターを持つ有効な共通言語ランタイム (CLR) メソッドシグネチャ。|有効なマネージ型のパラメーターを持つ有効な CLR メソッド シグネチャ。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|`miCil` と `miManaged` を設定します。|`miNative` と `miUnmanaged` を設定します。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
