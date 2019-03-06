---
title: IIdentityAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 263dc0f9d686440aaa23e359c26db1b4d3d09b1e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375970"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority インターフェイス

コード オブジェクトの id キーを管理します。

## <a name="methods"></a>メソッド

|メソッド|説明|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|2 つ指定されているかどうかを示す値を取得します[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)インスタンスが等しい。|
|`IIdentityAuthority::AreReferencesEqual`|2 つ指定されているかどうかを示す値を取得します[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)インスタンスが等しい。|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|2 つの指定した文字列の定義 id の形式が等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::AreTextualReferencesEqual`|2 つの指定した文字列の参照 id の形式が等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::CreateDefinition`|新しいポインターを取得します。 `IDefinitionIdentity` 、現在のスコープ内のコード オブジェクトを表すインスタンス。|
|`IIdentityAuthority::CreateReference`|新しいポインターを取得します。 `IReferenceIdentity` 、現在のスコープ内のコード オブジェクトを表すインスタンス。|
|`IIdentityAuthority::DefinitionToText`|指定した書式設定された文字列バージョンを取得`IDefinitionIdentity`します。|
|`IIdentityAuthority::DefinitionToTextBuffer`|指定した文字列形式を指定のワイド文字バッファーに設定`IDefinitionIdentity`します。|
|`IIdentityAuthority::DoesDefinitionMatchReference`|示す値を取得するかどうか、指定した`IDefinitionIdentity`と`IReferenceIdentity`インスタンスが同じコード オブジェクトを参照してください。|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|指定した文字列が同じコード オブジェクトを参照するかどうかを示す値を取得します。|
|`IIdentityAuthority::GenerateDefinitionKey`|指定した文字列が新しく作成されたキーへのポインターを取得`IDefinitionIdentity`します。|
|`IIdentityAuthority::GenerateReferenceKey`|指定した文字列が新しく作成されたキーへのポインターを取得`IReferenceIdentity`します。|
|`IIdentityAuthority::HashDefinition`|指定したハッシュ値を取得します。`IDefinitionIdentity`します。|
|`IIdentityAuthority::HashReference`|指定したハッシュ値を取得します。`IReferenceIdentity`します。|
|`IIdentityAuthority::ReferenceToText`|指定した書式設定された文字列バージョンを取得`IReferenceIdentity`します。|
|`IIdentityAuthority::ReferenceToTextBuffer`|指定した文字列形式を指定のワイド文字バッファーに設定`IReferenceIdentity`します。|
|`IIdentityAuthority::TextToDefinition`|インターフェイス ポインターを取得、`IDefinitionIdentity`書式指定文字列を指定された対象から生成されたインスタンス。|
|`IIdentityAuthority::TextToReference`|インターフェイス ポインターを取得、`IReferenceIdentity`書式指定文字列を指定された対象から生成されたインスタンス。|

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** Isolation.h

**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
