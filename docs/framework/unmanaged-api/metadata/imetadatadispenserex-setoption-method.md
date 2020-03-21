---
title: IMetaDataDispenserEx::SetOption メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
ms.openlocfilehash: f8e85a670d04e5825653864484b7ccd9ce747949
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175903"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption メソッド
指定されたオプションを、現在のメタデータ スコープの指定された値に設定します。 このオプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `optionId`  
 [in]設定するオプションを指定する GUID へのポインター。  
  
 `pValue`  
 [in]オプションの設定に使用する値。 この値の型は、指定されたオプションの型のバリアントである必要があります。  
  
## <a name="remarks"></a>解説  
 次の表に`optionId`、パラメーターが指すことができる使用可能な GUID と、パラメーターに対応する有効な`pValue`値を示します。  
  
|GUID|説明|`pValue`パラメーター|  
|----------|-----------------|------------------------|  
|メタデータチェック重複|重複をチェックする項目を制御します。 新しい項目を作成する[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)メソッドを呼び出すたびに、その項目が現在のスコープに既に存在するかどうかを確認するようにメソッドに要求できます。 たとえば、`mdMethodDef`アイテムの存在を確認できます。この場合[、IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)を呼び出すと、メソッドが現在のスコープに存在しないことを確認します。 このチェックでは、特定のメソッド (親の型、名前、およびシグネチャ) を一意に識別するキーを使用します。|型 UI4 のバリアントである必要があり、列挙体の値の組み合わせを含[める](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)必要があります。|  
|をチェックします。|参照先の項目を定義に変換するコントロール。 既定では、メタデータ エンジンは、参照先の項目が現在のスコープで実際に定義されている場合に、参照先の項目を定義に変換してコードを最適化します。|型 UI4 のバリアントである必要があり[、CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)列挙体の値の組み合わせを含める必要があります。|  
|トークンの動き|メタデータマージ中に発生するトークンの再マップがコールバックを生成する制御します。 [メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)を使用して[、IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)インターフェイスを確立します。|型 UI4 のバリアントである必要があり、[列挙](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)体の値の組み合わせを含める必要があります。|  
|メタデータセットエンク|エディット コンティニュ (ENC) の動作を制御します。 一度に設定できる動作モードは 1 つだけです。|UI4 型のバリアントである必要があり[、CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md)列挙体の値を含める必要があります。 値はビットマスクではありません。|  
|注文のエラーをエラーします。|出力された順序のエラーがコールバックを生成するコントロール。 メタデータの順序の変更は致命的ではありません。ただし、メタデータ エンジンが優先する順序でメタデータを出力する場合、メタデータはよりコンパクトであるため、より効率的に検索できます。 `IMetaDataEmit::SetHandler`このメソッドを使用して[、IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)インターフェイスを確立します。|型 UI4 のバリアントである必要があり、列挙体の値の組み合わせを含[める](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)必要があります。|  
|メタデータインポートオプション|ENC で削除されたアイテムの種類を列挙子によって取得するコントロール。|UI4 型のバリアントである必要があり[、CorImportOptions 列挙の](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)値の組み合わせを含める必要があります。|  
|メタデータスレッドセーフティオプション|メタデータ エンジンがリーダー/ライター ロックを取得するかどうかを制御します。 デフォルトでは、エンジンは、アクセスが呼び出し元によってシングルスレッドであると想定するため、ロックは取得されません。 メタデータ API を使用する場合、クライアントは適切なスレッド同期を維持する責任があります。|型 UI4 のバリアントである必要があり、値を含める必要があります、[コルスレッドセーフティ オプション列挙](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md)体。 値はビットマスクではありません。|  
|メタデータ生成TCEアダプター|タイプ ライブラリ インポーターが COM 接続ポイント コンテナの緊密結合イベント (TCE) アダプタを生成するかどうかを制御します。|BOOL 型のバリアントである必要があります。 に`pValue`設定`true`されている場合、タイプ ライブラリ インポーターは TCE アダプタを生成します。|  
|名前空間を指定します。|インポートするタイプ ライブラリの既定以外の名前空間を指定します。|ヌル値または BSTR 型のバリアントのいずれかでなければなりません。 null`pValue`値の場合、現在の名前空間は null に設定されます。それ以外の場合、現在の名前空間は、バリアントの BSTR 型に保持されている文字列に設定されます。|  
|メタデータリンカーのオプション|リンカーがアセンブリまたは .NET Framework モジュール ファイルを生成するかどうかを制御します。|型 UI4 のバリアントである必要があり[、CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)列挙体の値の組み合わせを含める必要があります。|  
|メタデータランタイムのバージョン|このイメージがビルドされた共通言語ランタイムのバージョンを指定します。 バージョンは、"v1.0.3705" などの文字列として格納されます。|ヌル値、VT_EMPTY値、または BSTR 型のバリアントでなければなりません。 null`pValue`の場合、ランタイム バージョンは null に設定されます。 VT_EMPTY`pValue`場合、バージョンは既定値に設定され、メタデータ コードが実行されている Mscorwks.dll のバージョンから取得されます。 それ以外の場合、ランタイム バージョンはバリアントの BSTR 型に保持されている文字列に設定されます。|  
|メタデータマージャーオプション|メタデータをマージするためのオプションを指定します。|UI4 型のバリアントである必要があり、CorHdr.h ファイルで説明`MergeFlags`されている列挙体の値の組み合わせを含める必要があります。|  
|ローカル参照|ローカル参照を定義に最適化できないようにします。|[列挙](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)体の値の組み合わせを含める必要があります。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
