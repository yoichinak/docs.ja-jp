---
title: Windows フォームでのより安全な印刷
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: b0387a82f142fb32912dad1370d6ac0c784e8894
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592640"
---
# <a name="more-secure-printing-in-windows-forms"></a>Windows フォームでのより安全な印刷
頻繁に、Windows フォーム アプリケーションには、印刷機能が含まれます。 .NET Framework を使用して、<xref:System.Drawing.Printing.PrintingPermission>クラスからの印刷機能へのアクセス制御および関連付けられている<xref:System.Drawing.Printing.PrintingPermissionLevel>アクセスのレベルを示す列挙値。 既定では、ローカルのイントラネットとインターネット ゾーンに既定では、印刷が有効になりますただし、どちらのゾーン レベルのアクセスが制限されています。 アプリケーションが印刷できるかどうか、ユーザーの介入が必要ですか、印刷は、アプリケーションに付与されるアクセス許可の値に依存できません。 ローカル イントラネット ゾーンでは既定では、<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>とイントラネット ゾーンのアクセスを受け取る<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>アクセスします。  
  
 次の表では、各印刷アクセス許可レベルで使用可能な機能を示します。  
  
|PrintingPermissionLevel|説明|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|インストールされているすべてのプリンターへのフル アクセスを提供します。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|既定のプリンターにプログラムによる印刷と制限の厳しい印刷ダイアログ ボックスを使用した安全な印刷できます。 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> のサブセットです。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|制限されたダイアログ ボックスからのみ印刷機能を提供します。 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> のサブセットです。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|プリンターにアクセスできなくなります。 <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> のサブセットです。|  
  
## <a name="see-also"></a>関連項目

- [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows フォームのセキュリティに関するその他の考慮事項](additional-security-considerations-in-windows-forms.md)
- [Windows フォームのセキュリティの概要](security-in-windows-forms-overview.md)
- [Windows フォームのセキュリティ](windows-forms-security.md)
