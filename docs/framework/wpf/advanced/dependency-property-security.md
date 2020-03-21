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
ms.openlocfilehash: f5640b348ccd68819052f58756489489371862d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186392"
---
# <a name="dependency-property-security"></a>依存関係プロパティのセキュリティ
依存関係プロパティは、一般に、パブリック プロパティと考える必要があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のプロパティ システムの性質のため、依存関係プロパティの値に関してセキュリティを保証することはできません。  

<a name="AccessSecurity"></a>
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>ラッパーと依存関係プロパティのアクセスとセキュリティ  
 通常、依存関係プロパティは、インスタンスからのプロパティの取得や設定を簡単にする "ラッパー" 共通言語ランタイム (CLR) プロパティと共に実装されます。 しかし、ラッパーは、依存関係プロパティとやり取りするときに使用<xref:System.Windows.DependencyObject.GetValue%2A>される<xref:System.Windows.DependencyObject.SetValue%2A>基になる呼び出しと静的な呼び出しを実装する便利なメソッドにすぎません。 別の方法では、プロパティは共通言語ランタイム (CLR) プロパティとして公開され、プライベート フィールドではなく依存関係プロパティによってサポートされます。 ラッパーに適用されるセキュリティ メカニズムでは、プロパティ システムの動作と基になっている依存関係プロパティのアクセスは並列化されません。 ラッパーにセキュリティ確認要求を配置すると、便利なメソッドの使用は妨げられるだけですが、 または<xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>の呼び出しは行いません。 同様に、保護されたアクセス レベルまたはプライベート アクセス レベルをラッパーに適用しても、効果的なセキュリティは提供されません。  
  
 独自の依存関係プロパティを記述する場合は、ラッパーと<xref:System.Windows.DependencyProperty>識別子フィールドをパブリック メンバーとして宣言し、呼び出し元がそのプロパティの実際のアクセス レベルに関する誤解を招く情報を取得しないようにする必要があります (そのストアは依存関係プロパティとして実装されているため)。  
  
 カスタム依存関係プロパティの場合、プロパティを読み取り専用の依存関係プロパティとして登録できます<xref:System.Windows.DependencyPropertyKey>。 詳細については、「[読み取り専用の依存関係プロパティ](read-only-dependency-properties.md)」を参照してください。  
  
> [!NOTE]
> 識別子フィールド<xref:System.Windows.DependencyProperty>のプライベート宣言は禁止されておらず、カスタム クラスのすぐに公開される名前空間を減らすために使用することもできますが、次のセクションで説明する理由から、共通言語ランタイム (CLR) 言語定義と同じ意味で、このようなプロパティを "private" と見なすべきではありません。  
  
<a name="PropertySystemExposure"></a>
## <a name="property-system-exposure-of-dependency-properties"></a>プロパティ システムによる依存関係プロパティの公開  
 一般的には有用ではなく、公開以外のアクセスレベルとして宣言することは誤解<xref:System.Windows.DependencyProperty>を招く可能性があります。 このようなアクセス レベルの設定は、宣言しているクラスからインスタンスへの参照を取得できるのを防ぐだけです。 しかし、プロパティ システムには、特定のプロパティを識別する<xref:System.Windows.DependencyProperty>手段として、クラスまたは派生クラスインスタンスのインスタンスに存在するを識別する手段として返すいくつかの側面があり、元の静的識別子が非パブリックとして<xref:System.Windows.DependencyObject.SetValue%2A>宣言されている場合でも、この識別子は呼び出しで使用できます。 また、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>仮想メソッドは、値を変更した既存の依存関係プロパティの情報を受け取ります。 さらに、このメソッド<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>は、ローカルに設定された値を持つインスタンス上の任意のプロパティの識別子を返します。  
  
### <a name="validation-and-security"></a>検証とセキュリティ  
 要求を a に<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>適用し、要求エラーで検証エラーが発生し、プロパティの設定を妨げる場合は、適切なセキュリティ メカニズムではありません。 また、アプリケーション ドメイン内で動作<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>している呼び出し元の場合、強制的に適用される値の無効化は、悪意のある呼び出し元によって抑制される可能性があります。  
  
## <a name="see-also"></a>関連項目

- [カスタム依存関係プロパティ](custom-dependency-properties.md)
