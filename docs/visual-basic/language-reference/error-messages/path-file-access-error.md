---
title: パス/ファイル アクセス エラー
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 4f18c9216aa24840bc205534a97124d12698cb98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799181"
---
# <a name="pathfile-access-error"></a>パス/ファイル アクセス エラー
ファイル アクセスまたはディスク アクセス操作中に、オペレーティング システムは、パスとファイル名の間の接続を作成できませんでした。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. ファイルの仕様が正しく書式設定を確認します。 ファイル名は、完全修飾 (絶対) または相対パスに含めることができますのパス。 (パスは、別のドライブ上にある) 場合、ドライブ名で完全修飾パスを開始し、ルートから、ファイルへの明示的なパスを一覧表示します。 完全に修飾されていない任意のパスでは、現在のドライブとディレクトリに対して相対的です。  
  
2. 既存の読み取り専用ファイルを置き換えるファイルの保存試みなかったことを確認します。 大文字と小文字の場合は、ターゲット ファイルの読み取り専用属性を変更または別のファイル名、ファイルを保存します。  
  
3. 順次読み取り専用のファイルを開くをしないようにするには必ず`Output`または`Append`モード。 この場合は、ファイルを開き`Input`モードまたはファイルの読み取り専用属性を変更します。  
  
4. データベースまたはドキュメント内での Visual Basic プロジェクトを変更しようとしてしなかったことを確認します。  
  
## <a name="see-also"></a>関連項目

- [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)
