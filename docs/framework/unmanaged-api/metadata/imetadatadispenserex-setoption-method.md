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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6916e6344fe5c112b216ca753c372fa73a4d5af5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777707"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption メソッド
現在のメタデータ スコープの指定した値に指定されたオプションを設定します。 オプションは、現在のメタデータ スコープへの呼び出しを処理する方法を制御します。  
  
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
 [in]オプションの設定に使用する値。 この値の型は、指定したオプションの種類の一種である必要があります。  
  
## <a name="remarks"></a>Remarks  
 次の表に、使用可能な Guid を`optionId`パラメーターが指すできますとの対応する有効な値、`pValue`パラメーター。  
  
|GUID|説明|`pValue` パラメーター|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|重複をチェックする項目を制御します。 呼び出すたびに、 [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)新しい項目を作成する方法、項目が現在のスコープに既に存在するかどうかを確認するメソッドを依頼することができます。 などの存在を確認できます`mdMethodDef`項目です。 この場合は、呼び出す[imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)、メソッドが現在のスコープに存在しないことを確認します。 このチェックは特定のメソッドを一意に識別するキーを使用して: 親の型、名、および署名されます。|UI4、型のバリアントにする必要があり、の値の組み合わせを含める必要があります、 [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)列挙体。|  
|MetaDataRefToDefCheck|参照項目コントロールは、定義に変換されます。 既定では、メタデータ エンジンは、参照されているアイテムが実際には、現在のスコープで定義されている場合、参照されているアイテムをその定義に変換することで、コードを最適化します。|UI4、型のバリアントにする必要があり、の値の組み合わせを含める必要があります、 [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)列挙体。|  
|MetaDataNotificationForTokenMovement|メタデータのマージ中に発生したトークンを再マップ コントロールでは、コールバックを生成します。 使用して、 [imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)を確立する方法、 [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)インターフェイス。|UI4、型のバリアントにする必要があり、の値の組み合わせを含める必要があります、 [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)列挙体。|  
|MetaDataSetENC|エディット コンティニュ (ENC) の動作を制御します。 一度に 1 つのモードの動作を設定できます。|UI4、型のバリアントにする必要があり、の値を含める必要があります、 [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md)列挙体。 値はビットマスクではありません。|  
|MetaDataErrorIfEmitOutOfOrder|出力-の順序を逸脱するエラー コールバックの生成を制御します。 誤順序のメタデータの生成致命的ではありません。ただし、メタデータ エンジンによって優先順序でのメタデータを生成するメタデータがコンパクトにし、そのためより効率的に検索できます。 使用して、`IMetaDataEmit::SetHandler`を確立する方法、 [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)インターフェイス。|UI4、型のバリアントにする必要があり、の値の組み合わせを含める必要があります、 [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)列挙体。|  
|MetaDataImportOption|列挙子によって取得 ENC 時に削除された項目の種類を制御します。|UI4、型のバリアントにする必要があり、の値の組み合わせを含める必要があります、 [CorImportOptions 列挙型](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)列挙体。|  
|MetaDataThreadSafetyOptions|メタデータ エンジンがスレッド セーフを積み重ねないロックについてリーダー/ライターを取得しているかどうかを制御します。 既定では、エンジンでは、ことへのアクセスはシングル スレッド、呼び出し元でロックは取得しないように想定しています。 クライアントは、メタデータ API を使用する場合は、適切なスレッド同期を保守する責任を負います。|UI4、型のバリアントにする必要があり、の値を含める必要があります、 [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md)列挙体。 値はビットマスクではありません。|  
|MetaDataGenerateTCEAdapters|タイプ ライブラリ インポーターが COM 接続ポイント コンテナーを密に結合されたイベント (TCE) アダプターを生成するかどうかを制御します。|BOOL 型のバリアントにする必要があります。 場合`pValue`に設定されている`true`、タイプ ライブラリ インポーターは TCE アダプターを生成します。|  
|MetaDataTypeLibImportNamespace|インポートされるタイプ ライブラリの既定以外の名前空間を指定します。|Null 値または BSTR 型のバリアント型のいずれかである必要があります。 場合`pValue`が null の値に null。 それ以外の場合、現在の名前空間が設定されて、現在の名前空間は、バリアントの BSTR 型に保持されている文字列に設定されます。|  
|MetaDataLinkerOptions|リンカーがアセンブリまたは .NET Framework のモジュール ファイルを生成するかどうかを制御します。|UI4、型のバリアントにする必要があり、の値の組み合わせを含める必要があります、 [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)列挙体。|  
|MetaDataRuntimeVersion|このイメージの作成対象となる共通言語ランタイムのバージョンを指定します。 バージョンは、"v1.0.3705"などの文字列として格納されます。|Null 値を VT_EMPTY 値、または BSTR 型のバリアントがあります。 場合`pValue`が null の場合、ランタイムのバージョンが設定を null にします。 場合`pValue`VT_EMPTY には、バージョンがあるメタデータのコードが実行されている Mscorwks.dll のバージョンから描画された既定値に設定します。 それ以外の場合、ランタイムのバージョンは、バリアントの BSTR 型に保持されている文字列に設定されます。|  
|MetaDataMergerOptions|メタデータをマージするためのオプションを指定します。|UI4、型のバリアントにする必要があり、の値の組み合わせを含める必要があります、`MergeFlags`列挙型では、CorHdr.h ファイルで説明されています。|  
|MetaDataPreserveLocalRefs|定義にローカル参照の最適化を無効にします。|値の組み合わせを含める必要があります、 [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)列挙体。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
