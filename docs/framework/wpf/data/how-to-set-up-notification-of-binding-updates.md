---
title: '方法: バインディングの更新の通知を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 4185198312ed98f9aaa1388626600d9f21abae55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051989"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>方法: バインディングの更新の通知を設定する
この例では、バインドのバインディング ターゲット (ターゲット) またはバインディング ソース (ソース) のプロパティが更新されたときに通知するように設定する方法を示します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、バインドのソースまたはターゲットが更新されるたびにデータ更新イベントを発生させます。 内部的には、このイベントは、バインドされたデータが変更されているため、更新する必要があることを [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に通知するために使用されます。 これらのイベントをするには、また、一方向または双方向のバインドが適切に機能が使用してデータ クラスを実装する必要がありますに注意してください、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイス。 詳細については、「[プロパティの変更通知を実装する](how-to-implement-property-change-notification.md)」を参照してください。  
  
 設定、<xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>または<xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>するプロパティ (または両方)`true`バインドにします。 このイベントをリッスンするために提供するハンドラーは、変更を通知する要素に直接アタッチするか、コンテキスト内の何かが変更されたことを認識する場合は、全体的なデータ コンテキストにアタッチする必要があります。  
  
 ターゲットのプロパティが更新されたときの通知を設定する方法の例を次に示します。  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 その後、EventHandler\<T> デリゲート (この例では *OnTargetUpdated*) に基づいて、イベントを処理するハンドラーを割り当てることができます。  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 イベントのパラメーターを使用して、変更されたプロパティの詳細 (型や、複数の要素に同じハンドラーがアタッチされている場合の特定の要素など) を確認できます。これは、1 つの要素に複数のバインドされたプロパティがある場合に役に立つ可能性があります。  
  
## <a name="see-also"></a>関連項目

- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
