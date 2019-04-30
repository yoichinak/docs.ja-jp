---
title: ICeeGen インターフェイス
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fb081c48abf899b44da1c1351efa3f6036f1c8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050208"
---
# <a name="iceegen-interface"></a>ICeeGen インターフェイス
動的なコード コンパイルのためのメソッドを提供します。  
  
 このインターフェイスは廃止され、使用する必要があります。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AddSectionReloc メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|互換性のために残されています。 コード ベースを .reloc 命令を追加します。|  
|[AllocateMethodBuffer メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|互換性のために残されています。 メソッドで指定されたサイズのバッファーを作成し、メソッドの相対仮想アドレスを取得します。|  
|[ComputePointer メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|互換性のために残されています。 指定したコードのセクションのバッファーを決定します。|  
|[EmitString メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|互換性のために残されています。 コード ベースに、指定した文字列を出力します。|  
|[GenerateCeeFile メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|互換性のために残されています。 これに現在読み込まれてコード ベースを含むコード ベースのファイルが生成されます`ICeeGen`します。|  
|[GenerateCeeMemoryImage メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|互換性のために残されています。 コード ベースのメモリ内には、イメージを生成します。|  
|[GetIlSection メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|互換性のために残されています。 指定したハンドルによって参照される基本の中間言語コードのセクションを取得します。|  
|[GetIMapTokenIface メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|互換性のために残されています。 指定したトークンによって参照されているインターフェイスを取得します。|  
|[GetMethodBuffer メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|互換性のために残されています。 指定の相対仮想アドレスにあるメソッドの適切なサイズのバッファーを取得します。|  
|[GetSectionBlock メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|互換性のために残されています。 コード ベースのセクションのブロックを取得します。|  
|[GetSectionCreate メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|互換性のために残されています。 生成し、指定した名前とフラグの値を使用してコードのセクションを取得します。|  
|[GetSectionDataLen メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|互換性のために残されています。 指定されたセクションの長さを取得します。|  
|[GetString メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|互換性のために残されています。 指定された相対仮想アドレスに格納されている文字列を取得します。|  
|[GetStringSection メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|互換性のために残されています。 指定したハンドルによって参照されるコードのセクションの文字列表現を取得します。|  
|[TruncateSection メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|互換性のために残されています。 指定された長さでは、指定したコードのセクションを切り捨てます。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
