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
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796427"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority インターフェイス

コードオブジェクトの id キーを管理します。

## <a name="methods"></a>メソッド

|メソッド|説明|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|指定した2つの[IDefinitionIdentity](idefinitionidentity-interface.md)インスタンスが等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::AreReferencesEqual`|指定した2つの[IReferenceIdentity](ireferenceidentity-interface.md)インスタンスが等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|指定した2つの文字列定義 id 表現が等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::AreTextualReferencesEqual`|指定した2つの文字列参照 id 表現が等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::CreateDefinition`|現在のスコープ内のコード`IDefinitionIdentity`オブジェクトを表す新しいインスタンスへのポインターを取得します。|
|`IIdentityAuthority::CreateReference`|現在のスコープ内のコード`IReferenceIdentity`オブジェクトを表す新しいインスタンスへのポインターを取得します。|
|`IIdentityAuthority::DefinitionToText`|指定したの書式設定され`IDefinitionIdentity`た文字列バージョンを取得します。|
|`IIdentityAuthority::DefinitionToTextBuffer`|指定したワイド文字バッファーに、指定`IDefinitionIdentity`したの文字列バージョンを格納します。|
|`IIdentityAuthority::DoesDefinitionMatchReference`|指定した`IDefinitionIdentity`と`IReferenceIdentity`インスタンスが同じコードオブジェクトを参照しているかどうかを示す値を取得します。|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|指定した文字列が同じコードオブジェクトを参照しているかどうかを示す値を取得します。|
|`IIdentityAuthority::GenerateDefinitionKey`|指定`IDefinitionIdentity`したに対して新しく作成された文字列キーへのポインターを取得します。|
|`IIdentityAuthority::GenerateReferenceKey`|指定`IReferenceIdentity`したに対して新しく作成された文字列キーへのポインターを取得します。|
|`IIdentityAuthority::HashDefinition`|指定した`IDefinitionIdentity`のハッシュ値を取得します。|
|`IIdentityAuthority::HashReference`|指定した`IReferenceIdentity`のハッシュ値を取得します。|
|`IIdentityAuthority::ReferenceToText`|指定したの書式設定され`IReferenceIdentity`た文字列バージョンを取得します。|
|`IIdentityAuthority::ReferenceToTextBuffer`|指定したワイド文字バッファーに、指定`IReferenceIdentity`したの文字列バージョンを格納します。|
|`IIdentityAuthority::TextToDefinition`|指定した書式設定さ`IDefinitionIdentity`れた文字列から生成されたインスタンスへのインターフェイスポインターを取得します。|
|`IIdentityAuthority::TextToReference`|指定した書式設定さ`IReferenceIdentity`れた文字列から生成されたインスタンスへのインターフェイスポインターを取得します。|

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** 分離 .h

**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
