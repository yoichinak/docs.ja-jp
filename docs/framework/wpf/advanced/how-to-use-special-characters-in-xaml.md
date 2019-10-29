---
title: '方法: XAML で特殊文字を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 713428adc2e1576d1b95984b492fe84c042c0a09
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919640"
---
# <a name="how-to-use-special-characters-in-xaml"></a>方法: XAML で特殊文字を使用する
Visual Studio で作成されたマークアップファイルは、Unicode UTF-8 ファイル形式で自動的に保存されます。つまり、アクセントマークなどのほとんどの特殊文字は正しくエンコードされます。 ただし、一般的に使用される一連の特殊文字で、別の方法で処理されるものがあります。 これらの特殊文字は、エンコードのために World Wide Web コンソーシアム (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 標準に従います。  
  
 この一連の特殊文字をエンコードするための構文を次の表に示します。  
  
|文字|構文|説明|  
|---------------|------------|-----------------|  
|<|`&lt;`|より小さい記号|  
|>|`&gt;`|より大きい記号|  
|&|`&amp;`|アンパサンド記号|  
|"|`&quot;`|二重引用符記号|  
  
> [!NOTE]
> Windows メモ帳などのテキストエディターを使用してマークアップファイルを作成する場合は、エンコードされた特殊文字を保持するために、Unicode UTF-8 ファイル形式でファイルを保存する必要があります。  
  
 次の例では、マークアップを作成するときにテキストで特殊文字を使用する方法を示します。  
  
## <a name="example"></a>例  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
