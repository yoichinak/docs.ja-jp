---
title: クリップボードの形式が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817179"
---
# <a name="clipboard-format-is-not-valid"></a>クリップボードの形式が有効ではありません。
指定されたクリップボードの形式は、実行中のメソッドと互換性がありません。 このエラーの考えられる原因には。  
  
-   クリップボードを使用して`GetText`または`SetText`メソッド以外のクリップボード形式を`vbCFText`または`vbCFLink`します。  
  
-   クリップボードを使用して`GetData`または`SetData`メソッド以外のクリップボード形式を`vbCFBitmap`、 `vbCFDIB`、または`vbCFMetafile`します。  
  
-   使用して、`GetData`または`SetData`のメソッド、`DataObject`登録されている形式 (& HC000 - & HFFFF)、Microsoft Windows によって予約された範囲内のクリップボード形式のときにそのクリップボードの形式で Microsoft Windows 登録されていません.  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   無効な形式を削除し、有効なものを指定します。  
  
## <a name="see-also"></a>関連項目

- [クリップボード:その他のデータ形式の追加](/cpp/mfc/clipboard-adding-other-formats)
