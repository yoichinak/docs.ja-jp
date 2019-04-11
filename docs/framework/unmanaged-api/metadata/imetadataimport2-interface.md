---
title: IMetaDataImport2 インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211933"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 インターフェイス
拡張、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)ジェネリック型の操作の機能を提供するインターフェイス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumGenericParamConstraints メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|指定したトークンによって表されるジェネリック パラメーターに関連付けられているジェネリック パラメーターの制約の配列の列挙子を取得します。|  
|[EnumGenericParams メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|トークンのジェネリック パラメーター トークンを指定した TypeDef または MethodDef に関連付けられた配列の列挙子を取得します。|  
|[EnumMethodSpecs メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|トークンに関連付けられた、指定した MethodDef または MemberRef MethodSpec トークンの配列の列挙子を取得します。|  
|[GetGenericParamConstraintProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|指定した制約トークンによって表されるジェネリック パラメーターの制約に関連付けられているメタデータを取得します。|  
|[GetGenericParamProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|指定したトークンによって表されるジェネリック パラメーターに関連付けられているメタデータを取得します。|  
|[GetMethodSpecProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|指定した MethodSpec によって参照されるメソッドのメタデータ署名のトークンを取得します。|  
|[GetPEKind メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|ポータブル実行可能 (PE) でコードの性質を識別する値ファイルを取得、通常、DLL または EXE ファイルの現在のメタデータ スコープで定義されています。|  
|[GetVersionString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|アセンブリのビルドに使用されたランタイムのバージョン番号を取得します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Reflection.PortableExecutableKinds>
- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
