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
ms.openlocfilehash: 85806ee9fb01cd2ca07697230c46a8847fdf8c6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053549"
---
# <a name="dependency-property-security"></a>依存関係プロパティのセキュリティ
依存関係プロパティは、一般に、パブリック プロパティと考える必要があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のプロパティ システムの性質のため、依存関係プロパティの値に関してセキュリティを保証することはできません。  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>ラッパーと依存関係プロパティのアクセスとセキュリティ  
 通常、依存関係プロパティは、インスタンスからのプロパティの取得または設定を簡素化する "ラッパー" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティと共に実装されます。 ただし、ラッパーは、基になるを実装するだけの簡易メソッド<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>依存関係プロパティと対話するときに使用される静的な呼び出しです。 別の考え方をすれば、プロパティは、プライベート フィールドではなくたまたま依存関係プロパティが基になっている [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティとして公開されます。 ラッパーに適用されるセキュリティ メカニズムでは、プロパティ システムの動作と基になっている依存関係プロパティのアクセスは並列化されません。 ラッパーのセキュリティ確認要求を配置することが便利なメソッドの使用状況を防ぐことのみがへの呼び出しを防ぐことはできません<xref:System.Windows.DependencyObject.GetValue%2A>または<xref:System.Windows.DependencyObject.SetValue%2A>します。 同様に、保護されたアクセス レベルまたはプライベート アクセス レベルをラッパーに適用しても、効果的なセキュリティは提供されません。  
  
 独自の依存関係プロパティを記述する場合は、ラッパーを宣言する必要があります、<xref:System.Windows.DependencyProperty>識別子は、呼び出し元誤解しないプロパティの真のアクセス レベルに関する情報 (そのストアの中のためにできるように、パブリック メンバーとしてフィールド実装されている依存関係プロパティとして)。  
  
 カスタム依存関係プロパティの場合、読み取り専用の依存関係プロパティとして、プロパティを登録することができ、これは、有効な手段への参照を保持していないすべてのユーザーが設定されるプロパティの防止、<xref:System.Windows.DependencyPropertyKey>プロパティ。 詳細については、「[読み取り専用の依存関係プロパティ](read-only-dependency-properties.md)」を参照してください。  
  
> [!NOTE]
>  宣言を<xref:System.Windows.DependencyProperty>識別子フィールドをプライベートは禁止されておらず、およびカスタム クラスをすぐに公開されている名前空間を減らすためにも使用できますが、このようなプロパティと見なすことと同じ意味で"private"、 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]言語定義では、次のセクションで説明した理由からそのアクセス レベルを定義します。  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>プロパティ システムによる依存関係プロパティの公開  
 一般的に実用的ではありませんし、可能性のある、誤解を招く宣言には、<xref:System.Windows.DependencyProperty>としてすべてのアクセス レベルのパブリック以外の場合。 このようなアクセス レベルの設定は、宣言しているクラスからインスタンスへの参照を取得できるのを防ぐだけです。 返すプロパティ システムのいくつかの側面がありますが、<xref:System.Windows.DependencyProperty>クラスのインスタンス、または派生クラスのインスタンスが存在し、この識別子で引き続き使用できるように、特定のプロパティを識別する手段として、<xref:System.Windows.DependencyObject.SetValue%2A>も呼び出す場合は、元の静的識別子が非パブリックとして宣言されています。 また、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>仮想メソッドは、値が変化した既存の依存関係プロパティの情報を受け取ります。 さらに、<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>メソッドは、ローカルに設定されたインスタンスで任意のプロパティの識別子を返しますの値。  
  
### <a name="validation-and-security"></a>検証とセキュリティ  
 要求を適用する<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>および、適切なセキュリティ メカニズムでないプロパティが設定されていることを防ぐために、必要に応じて失敗時に検証エラーを指定してください。 値の設定の無効化によって強制的に適用<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>呼び出しは、アプリケーション ドメイン内で動作している場合も、悪意のある呼び出し元に抑制でした。  
  
## <a name="see-also"></a>関連項目

- [カスタム依存関係プロパティ](custom-dependency-properties.md)
