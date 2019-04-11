---
title: IMetaDataEmit::MergeEnd メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 277e7e57ae01128039c3a280158110acde3363a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230006"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd メソッド
マージを現在のスコープを 1 つまたは複数の前の呼び出しで指定されたすべてのメタデータ スコープ[imetadataemit::merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT MergeEnd ();  
```  
  
## <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="remarks"></a>Remarks  
 このルーチンはトリガーのメタデータの実際の結合は、すべてのインポート前の呼び出しによって指定されたスコープ`IMetaDataEmit::Merge`出力の現在のスコープにします。  
  
 マージに、次の特殊な条件が適用されます。  
  
-   モジュールのバージョン id (MVID) は、インポート スコープ内のメタデータに一意であるため、まったくインポートします。  
  
-   既存のモジュール全体のプロパティは上書きされません。  
  
     モジュールのプロパティは、現在のスコープで既に設定された、モジュールのプロパティはインポートされません。 ただし、現在のスコープ内でモジュールのプロパティが設定されていない、最初に検出されたときに、一度だけがインポートされます。 これらのモジュールのプロパティが再度発生した場合、重複しています。 (MVID) を除くすべてのモジュールのプロパティの値が比較され、重複が見つからなかった場合、エラーが発生します。  
  
-   型の定義 (`TypeDef`)、現在のスコープに重複はマージされません。 `TypeDef` オブジェクトはそれぞれに対して重複をチェック*オブジェクトの完全修飾名* + *GUID* + *バージョン番号*します。 名前または GUID のいずれかで一致があるその他の 2 つの要素のいずれかが異なる場合、エラーが発生します。 それ以外の場合、3 つすべての項目が一致する場合`MergeEnd`エントリが重複しないことを確認する簡単なチェックがない場合、エラーが発生します。 この簡単なチェックを探します。  
  
    -   同じメンバー宣言を同じ順序で発生しています。 メンバーとしてフラグが付いている`mdPrivateScope`(を参照してください、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙型)。 この確認には含まれません特別にマージされます。  
  
    -   同じクラス レイアウト。  
  
     つまり、`TypeDef`オブジェクトする必要があります常に完全かつ一貫して定義するすべてのメタデータ スコープで宣言されている完全な定義があると見なされます (クラス) をそのメンバーの実装が複数のコンパイル単位に分散している場合。すべてのスコープに存在して各スコープには増分されません。 たとえば、パラメーター名、コントラクトに関連する場合が送出同様に、すべてのスコープに関連いない場合、それらがメタデータに出力しないする必要があります。  
  
     例外が、`TypeDef`オブジェクトとしてフラグが設定された増分のメンバーを持つことが`mdPrivateScope`します。 これらは、発生時に`MergeEnd`増分重複に関係なく、現在のスコープに追加します。 コンパイラは、プライベート スコープを認識するため、コンパイラはルールの適用を担当である必要があります。  
  
-   相対仮想アドレス (Rva) がインポートまたは; マージできません。コンパイラは、この情報を再生成が必要です。  
  
-   アタッチされている項目がマージされた場合にのみ、カスタム属性がマージされます。 たとえば、クラスに関連付けられているカスタム属性は、クラスが最初に検出されたときにマージされます。 カスタム属性が関連付けられている場合、`TypeDef`または`MemberDef`はマージされません、削除またはそのようなメタデータを更新するコンパイラの責任です (メンバーのコンパイルのタイムスタンプ) などのコンパイル単位に固有です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
