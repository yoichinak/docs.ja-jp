---
title: 'ベスト プラクティス : データ コントラクトのバージョン管理'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 4d500c37efa4a90e24b06cd2e886147e1f159d4e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320781"
---
# <a name="best-practices-data-contract-versioning"></a>ベスト プラクティス : データ コントラクトのバージョン管理
このトピックでは、長期的に容易に拡張させることのできるデータ コントラクトを作成するためのベスト プラクティスをいくつか紹介します。 データコントラクトの詳細については、「[データコントラクトの使用](./feature-details/using-data-contracts.md)」のトピックを参照してください。  
  
## <a name="note-on-schema-validation"></a>スキーマ検証に関する注意事項  
 データコントラクトのバージョン管理については、Windows Communication Foundation (WCF) によってエクスポートされるデータコントラクトスキーマにはバージョン管理サポートがないことに注意してください。既定では、要素は省略可能としてマークされています。  
  
 したがって、新しいデータ メンバーを追加するなどの一般的なバージョン管理シナリオであっても、スキーマに関してはシームレスに実装することはできません。 新しいバージョンのデータ コントラクト (この例ではデータ メンバーが追加されたもの) を、古いスキーマに基づいて検証することはできません。  
  
 ただし、スキーマへの厳密な準拠が要求されない場合も数多くあります。 ASP.NET を使用して作成された WCF および XML Web サービスを含む多くの Web サービスプラットフォームは、既定ではスキーマ検証を実行しないため、スキーマで記述されていない余分な要素を許容します。 このようなプラットフォームであればバージョン管理は容易です。  
  
 これらのことから、データ コントラクトのバージョン管理に関するガイドラインには、厳密なスキーマ検証が必要な場合とそうでない場合の 2 種類があります。  
  
## <a name="versioning-when-schema-validation-is-required"></a>スキーマ検証が必要な場合のバージョン管理  
 新から旧、旧から新の両方向で厳密なスキーマ検証が必要な場合、データ コントラクトは変更不可であると考えなければなりません。 バージョン管理が必要であれば、別の名前または名前空間で新しいデータ コントラクトを作成したうえで、そのデータ型が使用されているサービス コントラクトにバージョンを付ける必要があります。  
  
 たとえば、`PoProcessing` という発注書処理サービス コントラクトに対して、`PostPurchaseOrder` データ コントラクトに適合したパラメーターを受け取る `PurchaseOrder` という操作が定義されているとします。 `PurchaseOrder` コントラクトの内容を変更したい場合は、新しく `PurchaseOrder2` というデータ コントラクトを作成し、こちらに変更内容を含める必要があります。 そのうえで、サービス コントラクト レベルでバージョン管理を行う必要があります。 たとえば、`PostPurchaseOrder2` パラメーターを受け取る `PurchaseOrder2` 操作を別に作成するか、`PoProcessing2` サービス コントラクトを別途作成して `PostPurchaseOrder` 操作が `PurchaseOrder2` データ コントラクトを受け取るようにします。  
  
 なお、他のデータ コントラクトから参照されるデータ コントラクトに変更を施すと、サービス モデル レイヤーも拡張されます。 たとえば、先ほどの例で、`PurchaseOrder` データ コントラクトは変更の必要がないとします。 ただし、そのデータ メンバーである `Customer` データ コントラクトに、さらに `Address` データ コントラクトが含まれており、これを変更しなければならないとします。 この場合は、まず `Address2` というデータ コントラクトを別に作成して必要な変更を行います。次に `Customer2` というデータ コントラクトを作成し、`Address2` をそのデータ メンバーとして定義します。さらに、`PurchaseOrder2` というデータ コントラクトを作成して、`Customer2` をデータ メンバーとして定義します。 先ほどの例と同様、サービス コントラクトに対してもバージョン管理を行う必要があります。  
  
 ここまでの例では "2" を付けて名前を変えましたが、実際には、バージョン番号または日付を付加して、名前空間の方を変更するようお勧めします。 たとえば、`http://schemas.contoso.com/2005/05/21/PurchaseOrder` というデータ コントラクトを `http://schemas.contoso.com/2005/10/14/PurchaseOrder` に変更します。  
  
 詳細については、「ベストプラクティス:[サービスのバージョン管理](service-versioning.md)」を参照してください。  
  
 アプリケーションから送信するメッセージは厳密にスキーマに適合させる必要があるが、外部から受信したメッセージがこれに適合しているとは限らない、という場合もあります。 この場合、受信したメッセージには、異質なデータが含まれているおそれがあります。 余分な値は、WCF によって格納および返されるため、スキーマが無効なメッセージを送信します。 これを回避するには、ラウンド トリップ機能を無効にする必要があります。 これには、2 つの方法があります。  
  
- 独自に定義した型に <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装しない。  
  
- サービス コントラクトに <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を適用し、<xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> プロパティ値を `true` に設定する。  
  
 ラウンドトリップの詳細については、「[上位互換性のあるデータコントラクト](./feature-details/forward-compatible-data-contracts.md)」を参照してください。  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>スキーマ検証が不要な場合のバージョン管理  
 スキーマへの厳密な適合が求められるケースはそれほど多くありません。 多くのプラットフォームでは、スキーマに記述されていない余分な要素が許容されています。 これが許容される限り、「[データコントラクトのバージョン管理](./feature-details/data-contract-versioning.md)」および「[上位互換性のあるデータコントラクト](./feature-details/forward-compatible-data-contracts.md)」で説明されている機能の完全なセットを使用できます。 その場合は、以下のガイドラインに従うことをお勧めします。  
  
 旧バージョンの型が想定されている場所へ新バージョンの型を送信したり、新バージョンが想定されている場所へ旧バージョンを送信したりするには、いくつかのガイドラインに厳密に従う必要があります。 それ以外の項目への準拠は、それほど厳密には要求されませんが、これらはスキーマの将来的なバージョン管理に影響する可能性があります。  
  
1. 型の継承でデータ コントラクトをバージョン化してはいけません。 新バージョンを作成する場合は、既存の型のデータ コントラクトを直接変更するか、新しく型を定義してください。  
  
2. 継承とデータ コントラクトを併用してもかまいませんが、バージョン管理の目的で継承を使用しないことなど、いくつかの規則に従う必要があります。 ある型が基本型から派生している場合、その型は将来のバージョンで別の基本型から派生させてはいけません (データ コントラクトが同一である場合を除きます)。 例外として、階層内で、基本型と派生したデータ コントラクト型との間に別の型を追加することは可能です。ただし追加する型に含まれるデータ メンバーの名前は、階層内の他の型のどのバージョンに含まれるメンバーとも、同じにならないようにする必要があります。 一般に、同じ継承階層の異なるレベルで同名のデータ メンバーを使用すると、バージョン管理の上で重大な問題が生じるおそれがあります。  
  
3. ラウンド トリップが有効になるように、データ コントラクトの最初のバージョンから、必ず <xref:System.Runtime.Serialization.IExtensibleDataObject> を実装します。 詳細については、「[上位互換性のあるデータ コントラクト](./feature-details/forward-compatible-data-contracts.md)」を参照してください。 このインターフェイスが実装されていない型の 1 つ以上のバージョンがリリース済みである場合は、この型の次のバージョンで実装します。  
  
4. 新しいバージョンで、データ コントラクト名や名前空間を変更しないでください。 データ コントラクトの基になる型の名前や名前空間を変更する場合、<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> の <xref:System.Runtime.Serialization.DataContractAttribute> プロパティを使うなど、適切なメカニズムを使用して、データ コントラクト名と名前空間を残しておく必要があります。 名前付けの詳細については、「[データコントラクト名](./feature-details/data-contract-names.md)」を参照してください。  
  
5. 新しいバージョンで、データ メンバーの名前を変更しないでください。 データ メンバーの基になるフィールド、プロパティ、イベントの名前を変更する場合は、`Name` の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを使用して、既存のデータ メンバー名を残しておく必要があります。  
  
6. 新しいバージョンで、データ メンバーの基になるフィールド、プロパティ、イベントの型を変更して、そのデータ メンバーに対応するデータ コントラクトが変わってしまうようなことは避けてください。 予測されるデータ コントラクトを判断するうえで、インターフェイス型は <xref:System.Object> に相当することを念頭に置きます。  
  
7. 新しいバージョンで、<xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを調整して既存のデータ メンバーの順序を変えることは避けてください。  
  
8. 新しいバージョンで、新しいデータ メンバーを追加することは可能ですが、 以下の規則に従う必要があります。  
  
    1. <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティ値は、既定値である `false` のまま変更しないでください。  
  
    2. メンバーの既定値として `null` または 0 を許容できない場合は、<xref:System.Runtime.Serialization.OnDeserializingAttribute> を使用してコールバック メソッドを指定する必要があります。該当するメンバーが受信ストリーム内に含まれていない場合は、このコールバック メソッドで妥当な既定値を設定します。 コールバックの詳細については、「[バージョントレラントなシリアル化コールバック](./feature-details/version-tolerant-serialization-callbacks.md)」を参照してください。  
  
    3. 新しく追加されたすべてのデータメンバーが既存のデータメンバーの後に表示されるようにするには、<xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> プロパティを使用する必要があります。 これを実現するために、最初のバージョンのデータ コントラクトでは、どのデータ メンバーにも `Order` プロパティを設定しないことをお勧めします。 バージョン 2 のデータ コントラクトで追加されたすべてのデータ メンバーについては、`Order` プロパティを 2 に設定します。 バージョン 3 のデータ コントラクトで追加されたすべてのデータ メンバーについては、`Order` プロパティを 3 に設定します。以降のバージョンも同様にしていきます。 複数のデータ メンバーに同じ `Order` 番号を設定してかまいません。  
  
9. 新しいバージョンで、データ メンバーを削除しないでください。旧バージョンで、<xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティ値が `false` (既定値) であった場合も同様です。  
  
10. 既存のデータ メンバーの `IsRequired` プロパティ値をバージョンごとに変更しないでください。  
  
11. 必須データ メンバー (`IsRequired` の値が `true`) の場合、`EmitDefaultValue` プロパティ値をバージョンごとに変更しないでください。  
  
12. バージョン階層を分岐させないでください。 つまり、あるバージョンから別のバージョンへのパスは、このガイドラインで認められている変更のみを使用して、1 方向に 1 つのみになるようにします。  
  
     たとえば、Person データ コントラクトのバージョン 1 に、Name というデータ メンバーだけが定義されているとします。これに対し、Age というメンバーのみを追加したバージョン 2a と、Address というメンバーのみを追加したバージョン 2b を作成してはいけません。 2a から 2b に移行しようとすると、Age を削除して Address を追加することになります。この逆方向に移行する場合は、Address を削除して Age を追加しなければなりません。 このガイドラインでは、メンバーの削除が禁止されています。  
  
13. 一般に、アプリケーションの新しいバージョンで、既存のデータ コントラクト型のサブタイプを新たに作成することはできません。 同様に、Object 型またはインターフェイス型として宣言されたデータ メンバーの代わりに、新しいデータ コントラクトを作成して使うことはできません。 新規にクラスを定義できるのは、旧アプリケーションのすべてのインスタンスについて、既知の型リストにその新しい型を追加できることがわかっている場合に限ります。 たとえば、アプリケーションのバージョン 1 に LibraryItem というデータ コントラクト型があり、そのサブタイプとして Book および Newspaper が定義されているとします。 LibraryItem には、Book と Newspaper を含む既知の型のリストがあります。 この状況で、LibraryItem のサブタイプである Magazine をバージョン 2 に追加するとします。 バージョン 2 の Magazine のインスタンスをバージョン 1 に送信した場合、既知の型のリストに Magazine データ コントラクトが見つからないので、例外がスローされます。  
  
14. バージョン間で列挙型メンバーを追加または削除することはできません。 また、列挙型メンバーの名前を変更することもできません。ただし `EnumMemberAttribute` 属性の Name プロパティを使用して、データ コントラクト モデル内の名前を同じに保つ場合は例外です。  
  
15. コレクションは、「[データコントラクトのコレクション型](./feature-details/collection-types-in-data-contracts.md)」で説明されているように、データコントラクトモデルで交換できます。 これにより、高い柔軟性を実現できます。 ただし、バージョン間で交換できないような形でコレクション型を不用意に変更しないように注意してください。 たとえば、カスタマイズされていない (`CollectionDataContractAttribute` 属性がない) コレクションをカスタマイズされたコレクションに変更したり、カスタマイズされたコレクションをカスタマイズされていないコレクションに変更したりしないでください。 また、`CollectionDataContractAttribute` のプロパティをバージョンごとに変更しないでください。 許可されている変更は、Name プロパティまたは Namespace プロパティの追加だけです。この変更は、基になるコレクション型の名前または名前空間が変更されたとき、データ コントラクト名および名前空間を旧バージョンと同じにしておきたい場合に行います。  
  
 以上の中には、状況によっては従わなくてもよいガイドラインもあります。 その判断は、シリアル化、逆シリアル化、およびスキーマのメカニズムを完全に理解したうえで行ってください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [データ コントラクトの使用](./feature-details/using-data-contracts.md)
- [データ コントラクトのバージョン管理](./feature-details/data-contract-versioning.md)
- [データ コントラクト名](./feature-details/data-contract-names.md)
- [上位互換性のあるデータ コントラクト](./feature-details/forward-compatible-data-contracts.md)
- [バージョン トレラントなシリアル化コールバック](./feature-details/version-tolerant-serialization-callbacks.md)
