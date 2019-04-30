---
title: '方法: アプリケーション スコープのリソース ディクショナリを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 589e28b3c05496e3fc17055b98240e389faed068
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007488"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>方法: アプリケーション スコープのリソース ディクショナリを使用する
この例では、アプリケーション スコープのカスタム リソース ディクショナリを定義して、使用する方法を示します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Application> 共有リソースのアプリケーション スコープ ストアを公開します:<xref:System.Windows.Application.Resources%2A>します。 既定で、<xref:System.Windows.Application.Resources%2A>プロパティがのインスタンスで初期化されて、<xref:System.Windows.ResourceDictionary>型。 Get を使用してアプリケーション スコープのプロパティを設定すると、このインスタンスを使用する<xref:System.Windows.Application.Resources%2A>します。 詳細については、「[方法 :取得および設定、アプリケーション スコープ リソース](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100))します。
  
 使用して設定する複数のリソースがある場合<xref:System.Windows.Application.Resources%2A>、カスタム リソース ディクショナリは、これらのリソースを格納し、設定する代わりに使用できます<xref:System.Windows.Application.Resources%2A>を代わりにします。 XAML を使用してカスタム リソース ディクショナリを宣言する方法を次に示します。
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 使用して全体のリソース ディクショナリのスワップ<xref:System.Windows.Application.Resources%2A>各テーマが 1 つのリソース ディクショナリでカプセル化、アプリケーション スコープのテーマをサポートすることができます。 <xref:System.Windows.ResourceDictionary> を設定する方法を次の例に示します。  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 によって公開されているリソース ディクショナリからアプリケーション スコープのリソースを取得する方法を次に示します<xref:System.Windows.Application.Resources%2A>XAML でします。  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 コードでリソースも取得する方法を次に示します。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 使用するときに 2 つの考慮事項があります<xref:System.Windows.Application.Resources%2A>します。 まず、ディクショナリ*キー*オブジェクトは両方の設定とプロパティ値を取得するときに正確に同じオブジェクト インスタンスを使用する必要があります。 (キーに文字列を使用する場合、大文字と小文字が区別されることに注意してください)。2 つ目は、ディクショナリ*値*オブジェクトはプロパティ値を取得するときに、目的の型に値を変換する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [XAML リソース](../advanced/xaml-resources.md)
- [マージされたリソース ディクショナリ](../advanced/merged-resource-dictionaries.md)
