---
title: '方法: ファイル関連のダイアログ ボックスの自動アップグレードを無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: a4be35617e8be1c6c83ac6f2d06e03b6cbb2977f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769412"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>方法: ファイル関連のダイアログ ボックスの自動アップグレードを無効にする
ときに、<xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>クラスは、アプリケーションで使用されて、外観と動作は、アプリケーションがで実行されている Windows のバージョンによって異なります。 アプリケーションが作成されているときに、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]に表示される前または[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]、<xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>で自動的に表示される、[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]外観と動作します。 以降では、 [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)]、表示する自動アップグレードをオプトアウトすることができます、<xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>で、 [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-スタイルの外観と動作します。  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>ファイル関連のダイアログ ボックスの自動アップグレードを無効にするには  
  
1. 設定、<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>プロパティの<xref:System.Windows.Forms.OpenFileDialog>または<xref:System.Windows.Forms.SaveFileDialog>に`false` ダイアログ ボックスを表示する前にします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FileDialog>
