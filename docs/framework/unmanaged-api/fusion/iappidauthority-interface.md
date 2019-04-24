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
ms.openlocfilehash: 724ee01e91f1e9f4e34d2262610152a977ed4f53
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206656"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority インターフェイス
アプリケーション id と参照キーの比較を生成するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|2 つ指定されているかどうかを示す値を取得します[IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)インスタンスが等しい。 それらのそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION フラグの値を渡すことができます。|  
|`IAppIdAuthority::AreReferencesEqual`|2 つ指定されているかどうかを示す値を取得します[IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)インスタンスが等しい。 それらのそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION フラグの値を渡すことができます。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|2 つの指定した文字列の定義が等しいかどうかを示す値を取得します。 それらのそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION フラグの値を渡すことができます。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|指定した文字列の 2 つの参照が等しいかどうかを示す値を取得します。 それらのそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION フラグの値を渡すことができます。|  
|`IAppIdAuthority::CreateDefinition`|新しく生成されたインターフェイス ポインターを取得`IDefinitionAppId`を現在のスコープ内のアセンブリを表すインスタンス。|  
|`IAppIdAuthority::CreateReference`|新しく作成されたインターフェイス ポインターを取得`IReferenceAppId`を現在のスコープ内のアセンブリを表します。|  
|`IAppIdAuthority::DefinitionToText`|指定した文字列形式を取得`IDefinitionAppId`、指定したフラグの値を使用します。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|示す値を取得するかどうか、指定した`IDefinitionAppId`と`IReferenceAppId`同じアセンブリを表します。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|指定した定義の文字列と参照文字列が同じアセンブリを表すかどうかを示す値を取得します。|  
|`IAppIdAuthority::GenerateDefinitionKey`|表す、指定した文字列のキーを取得します。`IDefinitionAppId`インスタンス。|  
|`IAppIdAuthority::GenerateReferenceKey`|表す、指定した文字列のキーを取得します。`IReferenceAppId`インスタンス。|  
|`IAppIdAuthority::HashDefinition`|指定したハッシュ キーの取得`IDefinitionAppId`インスタンス。|  
|`IAppIdAuthority::HashReference`|指定したハッシュ キーの取得`IReferenceAppId`インスタンス。|  
|`IAppIdAuthority::ReferenceToText`|指定した文字列形式を取得`IReferenceAppId`、指定したフラグの値を使用します。|  
|`IAppIdAuthority::TextToDefinition`|インターフェイス ポインターを取得、`IDefinitionAppId`文字列の指定したキーによって参照されるアセンブリを表すインスタンス。|  
|`IAppIdAuthority::TextToReference`|インターフェイス ポインターを取得、`IReferenceAppId`文字列の指定したキーによって参照されるアセンブリを表すインスタンス。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
