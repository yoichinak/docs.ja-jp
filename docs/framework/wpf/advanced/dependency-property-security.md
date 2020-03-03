---
title: 依存関係プロパティのセキュリティ
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: d9dd9306980b80f7845c10e8c0ccb59f29821245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940839"
---
# <a name="dependency-property-security"></a>依存関係プロパティのセキュリティ
依存関係プロパティは、一般に、パブリック プロパティと考える必要があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のプロパティ システムの性質のため、依存関係プロパティの値に関してセキュリティを保証することはできません。  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>ラッパーと依存関係プロパティのアクセスとセキュリティ  
 通常、依存関係プロパティは、インスタンスからのプロパティの取得または設定を簡略化する "ラッパー" 共通言語ランタイム (CLR) プロパティと共に実装されます。 ただし、ラッパーは、依存関係プロパティを操作するとき<xref:System.Windows.DependencyObject.GetValue%2A>に<xref:System.Windows.DependencyObject.SetValue%2A>使用される、基になる呼び出しと静的呼び出しを実装する便利なメソッドにすぎません。 別の方法で考えると、プロパティは、プライベートフィールドではなく、依存関係プロパティによってサポートされる共通言語ランタイム (CLR) プロパティとして公開されます。 ラッパーに適用されるセキュリティ メカニズムでは、プロパティ システムの動作と基になっている依存関係プロパティのアクセスは並列化されません。 ラッパーにセキュリティ要求を配置すると、便宜的なメソッドの使用は禁止されますが、 <xref:System.Windows.DependencyObject.GetValue%2A>また<xref:System.Windows.DependencyObject.SetValue%2A>はの呼び出しを防ぐことはできません。 同様に、保護されたアクセス レベルまたはプライベート アクセス レベルをラッパーに適用しても、効果的なセキュリティは提供されません。  
  
 独自の依存関係プロパティを作成する場合は、ラッパーおよび<xref:System.Windows.DependencyProperty>識別子フィールドをパブリックメンバーとして宣言して、呼び出し元がそのプロパティの真のアクセスレベルに関する誤った情報を取得しないようにする必要があります (ストアがであるため)。依存関係プロパティとして実装されます)。  
  
 カスタム依存関係プロパティの場合は、プロパティを読み取り専用の依存関係プロパティとして登録できます。これにより、 <xref:System.Windows.DependencyPropertyKey>プロパティのへの参照を保持していないすべてのユーザーによってプロパティが設定されるのを防ぐことができます。 詳細については、「[読み取り専用の依存関係プロパティ](read-only-dependency-properties.md)」を参照してください。  
  
> [!NOTE]
> <xref:System.Windows.DependencyProperty>識別子フィールド private の宣言は禁止されていないため、カスタムクラスのすぐに公開される名前空間を減らすために使用される場合がありますが、このようなプロパティは、共通言語と同じ意味で "プライベート" と見なされないようにする必要があります。ランタイム (CLR) 言語定義では、次のセクションで説明する理由により、そのアクセスレベルが定義されます。  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>プロパティ システムによる依存関係プロパティの公開  
 一般には役に立ちません。また、を<xref:System.Windows.DependencyProperty> public 以外のアクセスレベルとして宣言することは誤解される可能性があります。 このようなアクセス レベルの設定は、宣言しているクラスからインスタンスへの参照を取得できるのを防ぐだけです。 ただし、プロパティシステムには、クラスのインスタンスまたは派生<xref:System.Windows.DependencyProperty>クラスのインスタンスに存在する特定のプロパティを識別する手段としてを返すいくつかの側面があります。この識別子は、 <xref:System.Windows.DependencyObject.SetValue%2A>呼び出しでも使用できます。元の静的識別子が非パブリックとして宣言されている場合は。 また、 <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>仮想メソッドは、値が変更された既存の依存関係プロパティの情報を受け取ります。 また、メソッドは<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> 、ローカルに設定された値を持つインスタンスの任意のプロパティの識別子を返します。  
  
### <a name="validation-and-security"></a>検証とセキュリティ  
 要求をに<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>適用し、要求失敗時に検証エラーが発生してプロパティが設定されないようにすることは、適切なセキュリティメカニズムではありません。 によって適用<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>される設定値の無効化は、悪意のある呼び出し元がアプリケーションドメイン内で動作している場合に、悪意のある呼び出し元によって抑制されることもあります。  
  
## <a name="see-also"></a>関連項目

- [カスタム依存関係プロパティ](custom-dependency-properties.md)
