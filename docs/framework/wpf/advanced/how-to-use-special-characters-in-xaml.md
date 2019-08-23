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
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918443"
---
# <a name="how-to-use-special-characters-in-xaml"></a>方法: XAML で特殊文字を使用する
で[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]作成されたマークアップファイルは、自動的[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]に utf-8 ファイル形式で保存されます。つまり、アクセントマークなどのほとんどの特殊文字は正しくエンコードされます。 ただし、一般的に使用される一連の特殊文字で、別の方法で処理されるものがあります。 これらの特殊文字は[!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] 、 [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)]エンコードの標準に従います。  
  
 この一連の特殊文字をエンコードするための構文を次の表に示します。  
  
|文字|構文|説明|  
|---------------|------------|-----------------|  
|<|`&lt;`|より小さい記号|  
|>|`&gt;`|より大きい記号|  
|&|`&amp;`|アンパサンド記号|  
|"|`&quot;`|二重引用符記号|  
  
> [!NOTE]
> Windows メモ帳などのテキストエディターを使用してマークアップファイルを作成する場合は、エンコードされ[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]た特殊文字を保持するために、ファイルを utf-8 ファイル形式で保存する必要があります。  
  
 次の例では、マークアップを作成するときにテキストで特殊文字を使用する方法を示します。  
  
## <a name="example"></a>例  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
