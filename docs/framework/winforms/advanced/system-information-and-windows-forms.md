---
title: システム情報と Windows フォーム
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: 2edc2e867259f8884467c3d5b0ae3d22ba391a77
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380116"
---
# <a name="system-information-and-windows-forms"></a>システム情報と Windows フォーム
コードで決定するために、アプリケーションが実行されているコンピューターに関する情報を収集するために必要な場合があります。 たとえば、のみ、特定のネットワークのドメインに接続しているときに適用される関数がある可能性があります。ここでドメインを確認して、ドメインが存在しない場合、関数を無効にする方法する必要があります。  
  
 Windows フォーム アプリケーションを使用できる、<xref:System.Windows.Forms.SystemInformation>クラスを実行時にさまざまなコンピューターに関する考慮事項を確認します。 次の例を使用して、<xref:System.Windows.Forms.SystemInformation>を取得するクラス、<xref:System.Windows.Forms.SystemInformation.UserName%2A>と<xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 すべてのメンバー、<xref:System.Windows.Forms.SystemInformation>クラスは読み取り専用はユーザーの設定を変更することはできません。 コンピューターに接続されているモニターの数からすべての情報を返すクラスの 100 を超えるメンバーが (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) に Windows エクスプ ローラーのアイコンの間隔 (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A>と<xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>)。  
  
 いくつかの便利なメンバーの<xref:System.Windows.Forms.SystemInformation>クラスが含まれて<xref:System.Windows.Forms.SystemInformation.ComputerName%2A>、 <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>、 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>、および<xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SystemInformation>
- [Windows フォームでの電源管理](power-management-in-windows-forms.md)
