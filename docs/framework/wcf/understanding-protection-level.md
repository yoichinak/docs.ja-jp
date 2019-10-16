---
title: 保護レベルの理解
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 896b75d3dfb5ebace9bef0c410e4a86dfb765bd8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321528"
---
# <a name="understanding-protection-level"></a>保護レベルの理解

`ProtectionLevel` プロパティは、<xref:System.ServiceModel.ServiceContractAttribute> クラス、<xref:System.ServiceModel.OperationContractAttribute> クラスなど、多くのクラスで使用されています。 このプロパティは、メッセージの一部または全体を保護する方法を制御します。 このトピックでは、Windows Communication Foundation (WCF) 機能とそのしくみについて説明します。

保護レベルの設定方法については、「[方法: ProtectionLevel プロパティを設定する](how-to-set-the-protectionlevel-property.md)」を参照してください。

> [!NOTE]
> 保護レベルは構成ではなく、コードでのみ設定できます。

## <a name="basics"></a>基本

保護レベル機能には、次の基本的な原則が適用されます。

- メッセージのどの部分の保護にも、3 つの基本レベルがあります。 このプロパティは、必ず、<xref:System.Net.Security.ProtectionLevel> 列挙値の 1 つに設定されます。 以下に、これらの値を保護の弱いものから順に示します。

  - `None`.

  - `Sign`. 保護された部分はデジタル署名されます。 これによって、保護されたメッセージ部分に対する改ざんが確実に検出されます。

  - `EncryptAndSign`. メッセージ部分は、署名される前に機密性を保証するために暗号化されます。

- この機能を使用すると、*アプリケーションデータ*に対してのみ保護要件を設定できます。 たとえば、WS-Addressing ヘッダーは、インフラストラクチャ データであるため、`ProtectionLevel` の影響を受けません。

- セキュリティ モードが `Transport` に設定されている場合は、メッセージ全体がトランスポート メカニズムで保護されます。 したがって、メッセージの異なる部分に別々の保護レベルを設定しても効果はありません。

- @No__t 0 は、バインディングが従う必要がある*最小レベル*を開発者が設定する方法です。 サービスの展開時に、構成内で指定されている実際のバインドは、最低レベルをサポートしている場合もあれば、サポートしていない場合もあります。 たとえば、<xref:System.ServiceModel.BasicHttpBinding> クラスは既定の設定ではセキュリティを提供しません (提供するように設定することもできます)。 そのため、`None` 以外に設定したコントラクトとこのバインドを使用すると、例外がスローされます。

- すべてのメッセージに対する最小 `ProtectionLevel` が `Sign` であることがサービスで要求されている場合、(WCF 以外のテクノロジによって作成された) クライアントはすべてのメッセージを暗号化して署名できます (これは最低限必要なものではありません)。 この場合、クライアントが最小値を超えているため、WCF は例外をスローしません。 ただし、WCF アプリケーション (サービスまたはクライアント) は、可能な場合はメッセージ部分を過剰にセキュリティで保護しませんが、最小レベルに準拠することに注意してください。 また、セキュリティ モードとして `Transport` を使用すると、トランスポートをより詳細なレベルで保護できないため、メッセージ ストリームを過剰に保護する可能性があることに注意してください。

- `ProtectionLevel` を明示的に `Sign` と `EncryptAndSign` のいずれかに設定する場合、セキュリティを有効にしたバインドを使用する必要があります。使用しない場合は、例外がスローされます。

- セキュリティを有効にしたバインドを選択し、コントラクト上のどこにも `ProtectionLevel` プロパティを設定しない場合は、すべてのアプリケーション データが暗号化および署名されます。

- セキュリティを無効にしたバインド (たとえば、`BasicHttpBinding` クラスは既定でセキュリティが無効に設定されています) を選択し、`ProtectionLevel` を明示的に設定しない場合は、どのアプリケーション データも保護されません。

- トランスポート レベルでセキュリティを適用するバインドを使用している場合、すべてのアプリケーション データは、トランスポートの機能に準じてセキュリティ保護されます。

- メッセージ レベルでセキュリティを適用するバインドを使用している場合、アプリケーション データは、コントラクトに設定された保護レベルに準じてセキュリティ保護されます。 保護レベルを指定しない場合、メッセージ内のすべてのアプリケーション データが暗号化および署名されます。

- `ProtectionLevel` は、異なるスコープ レベルに設定することができます。 スコープが関連付けられている階層構造については、次のセクションで説明します。

## <a name="scoping"></a>スコープ

`ProtectionLevel` を最上位の API に設定すると、その下位のすべての階層がそのレベルに設定されます。 より下位の階層で `ProtectionLevel` を別の値に設定すると、それ以下の階層のすべての API が新しいレベルにリセットされます (それより上位の階層の API は、引き続き最上位での設定に従います)。 階層を次に示します。 同じレベルの属性は、同等です。

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a>ProtectionLevel のプログラミング

階層内のいずれかの位置で `ProtectionLevel` をプログラムするには、属性の適用時にこのプロパティを適切な値に設定します。 例については、「[方法: ProtectionLevel プロパティを設定する](how-to-set-the-protectionlevel-property.md)」を参照してください。

> [!NOTE]
> フォールトおよびメッセージ コントラクトにプロパティを設定するには、これらの機能を理解する必要があります。 詳細については、「[方法: ProtectionLevel プロパティを設定](how-to-set-the-protectionlevel-property.md)する」および「[メッセージコントラクトの使用](./feature-details/using-message-contracts.md)」を参照してください。

## <a name="ws-addressing-dependency"></a>WS-Addressing の依存関係

ほとんどの場合、 [ServiceModel メタデータユーティリティツール (svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)を使用してクライアントを生成することで、クライアントコントラクトとサービスコントラクトが同一であることが保証されます。 ただし、同じように見えるコントラクトによって、クライアントから例外がスローされる場合があります。 これが発生するのは、バインディングが WS-Addressing 仕様をサポートせず、コントラクトで複数レベルの保護が指定されている場合です。 たとえば、<xref:System.ServiceModel.BasicHttpBinding> クラスはこの仕様をサポートしておらず、また WS-Addressing をサポートしないカスタム バインディングが作成されている場合もあります。 `ProtectionLevel` 機能は、WS-Addressing 仕様に依存して 1 つのコントラクトでさまざまな保護レベルを有効にします。 バインディングが WS-Addressing 仕様をサポートしない場合は、すべてのレベルが同一の保護レベルに設定されます。 コントラクトのすべてのスコープに対して有効な保護レベルは、コントラクトで使用されている最も強力な保護レベルに設定されます。

これにより、一見するとデバッグが困難な問題が発生する場合があります。 複数のサービスに適合するメソッドを含むクライアント コントラクト (インターフェイス) を作成できます。 つまり、同一のインターフェイスを使用して、多くのサービスと通信するクライアントを作成し、この 1 つのインターフェイスに、すべてのサービスに適合するメソッドを格納します。 このまれなシナリオでは、特定のサービスに適合するメソッドだけを呼び出すように注意する必要があります。 バインディングが <xref:System.ServiceModel.BasicHttpBinding> クラスの場合は、複数の保護レベルはサポートされません。 ただし、クライアントに応答するサービスは、必要な保護レベルよりも低い保護レベルを使用してクライアントに応答する場合もあります。 この場合、クライアントは、より高い保護レベルを求めているため例外をスローします。

この問題をコード例で示します。 次の例は、サービスとクライアント コントラクトを示しています。 バインドが[\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md)要素であると仮定します。 したがって、コントラクトでのすべての操作に同一の保護レベルが割り当てられます。 この同一の保護レベルは、すべての操作での最大保護レベルとして決定されます。

サービス コントラクトは次のとおりです。

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

次のコードは、クライアント コントラクト インターフェイスを示しています。 このコードには、別のサービスで使用するための `Tax` メソッドが含まれることに注意してください。

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

クライアントが `Price` メソッドを呼び出し、サービスから応答を受け取ると、例外をスローします。 例外をスローするのは、クライアントが `ProtectionLevel` で `ServiceContractAttribute` を指定していないため、<xref:System.Net.Security.ProtectionLevel.EncryptAndSign> メソッドを含むすべてのメソッドに既定値 (`Price`) を使用するからです。 ただし、保護レベルが <xref:System.Net.Security.ProtectionLevel.Sign> に設定された 1 つのメソッドがサービス コントラクトで定義されているため、サービスは、<xref:System.Net.Security.ProtectionLevel.Sign> レベルを使用して値を返します。 この場合、クライアントは、サービスからの応答を検証するときにエラーをスローします。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [サービスのセキュリティ保護](securing-services.md)
- [方法: ProtectionLevel プロパティを設定する](how-to-set-the-protectionlevel-property.md)
- [コントラクトおよびサービスのエラーの指定と処理](specifying-and-handling-faults-in-contracts-and-services.md)
- [メッセージ コントラクトの使用](./feature-details/using-message-contracts.md)
