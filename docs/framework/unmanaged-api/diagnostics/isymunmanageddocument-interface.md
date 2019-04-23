---
title: ISymUnmanagedDocument インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168806"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument インターフェイス
シンボル ストアによって参照されるドキュメントを表します。 ドキュメントは、uniform resource locator (URL) と GUID のドキュメントの種類によって定義されます。 URL を使用して格納する方法に関係なく、ドキュメントを検索でき、ドキュメントの種類の GUID。 ドキュメントのソースをシンボル ストアに格納でき、このインターフェイスを通じて取得できます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FindClosestLine メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|行を指定したシーケンス ポイントができない可能性がありますが、このドキュメントでは、シーケンス ポイントである最も近い行を返します。|  
|[GetCheckSum メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|チェックサムを取得します。|  
|[GetCheckSumAlgorithmId メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|チェックサム アルゴリズム識別子を取得またはチェックサムがない場合は、すべてゼロの GUID を返します。|  
|[GetDocumentType メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|このドキュメントのドキュメントの種類を取得します。|  
|[GetLanguage メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|このドキュメントの言語識別子を取得します。|  
|[GetLanguageVendor メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|このドキュメントの言語の販売元を取得します。|  
|[GetSourceLength メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|埋め込まれたソースの長さをバイト数で取得します。|  
|[GetSourceRange メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|指定されたバッファーに埋め込みのソースの指定した範囲を返します。|  
|[GetURL メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|このドキュメントの URL を返します。|  
|[HasEmbeddedSource メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|返します`true`ドキュメントが、デバッグのシンボルに埋め込まれたソースを返しますそれ以外の場合、`false`します。|  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
