---
title: IAppIdAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91ab2f71e7fb74f8e0e517b566d46d61c316ebe2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796842"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority インターフェイス
アプリケーション id と参照のキーを生成して比較するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|指定した2つの[IDefinitionAppId](idefinitionappid-interface.md)インスタンスが等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::AreReferencesEqual`|指定した2つの[IReferenceAppId](ireferenceappid-interface.md)インスタンスが等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|指定した2つの文字列定義が等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|指定した2つの文字列参照が等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::CreateDefinition`|現在のスコープ内のアセンブリを表す`IDefinitionAppId` 、新しく生成されたインスタンスへのインターフェイスポインターを取得します。|  
|`IAppIdAuthority::CreateReference`|現在のスコープ内のアセンブリを表す`IReferenceAppId` 、新しく作成されたへのインターフェイスポインターを取得します。|  
|`IAppIdAuthority::DefinitionToText`|指定したフラグ値を使用`IDefinitionAppId`して、指定したの文字列バージョンを取得します。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|指定した`IDefinitionAppId`と`IReferenceAppId`が同じアセンブリを表しているかどうかを示す値を取得します。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|指定した定義文字列と参照文字列が同じアセンブリを表しているかどうかを示す値を取得します。|  
|`IAppIdAuthority::GenerateDefinitionKey`|指定した`IDefinitionAppId`インスタンスを表す文字列キーを取得します。|  
|`IAppIdAuthority::GenerateReferenceKey`|指定した`IReferenceAppId`インスタンスを表す文字列キーを取得します。|  
|`IAppIdAuthority::HashDefinition`|指定した`IDefinitionAppId`インスタンスのハッシュキーを取得します。|  
|`IAppIdAuthority::HashReference`|指定した`IReferenceAppId`インスタンスのハッシュキーを取得します。|  
|`IAppIdAuthority::ReferenceToText`|指定したフラグ値を使用`IReferenceAppId`して、指定したの文字列バージョンを取得します。|  
|`IAppIdAuthority::TextToDefinition`|指定した文字列キーに`IDefinitionAppId`よって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。|  
|`IAppIdAuthority::TextToReference`|指定した文字列キーに`IReferenceAppId`よって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
