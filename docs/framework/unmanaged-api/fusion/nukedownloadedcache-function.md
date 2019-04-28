---
title: NukeDownloadedCache 関数
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e549e13c0d51e4aa708a674a2224168ab66f8ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774531"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache 関数
共通言語ランタイム (CLR) のダウンロード キャッシュを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、WinError.h で定義されている標準の COM エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 CLR のダウンロード キャッシュは、再利用できる場合、URL からダウンロードされる厳密な名前のアセンブリが格納領域です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** Fusion.dll と Mscorwks.dll します。 Mscorwks.dll のではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認します。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CreateHistoryReader 関数](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [GetHistoryFileDirectory 関数](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
