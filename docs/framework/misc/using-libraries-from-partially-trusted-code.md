---
title: 部分信頼コードからのライブラリの使用
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a3bbbaa565a6c118082456a1ab6d7af59db7067
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119276"
---
# <a name="using-libraries-from-partially-trusted-code"></a>部分信頼コードからのライブラリの使用
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  このトピックでは、厳密な名前付きアセンブリの動作に対処しにのみ適用されます[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md)アセンブリ。 [透過的セキュリティ コード、レベル 2](../../../docs/framework/misc/security-transparent-code-level-2.md)内のアセンブリ、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]または後での影響を受けない厳密な名前。 セキュリティ システムへの変更の詳細については、次を参照してください。[セキュリティ変更](../../../docs/framework/security/security-changes.md)します。  
  
 ホストまたはサンドボックスから不完全な信頼を受けているアプリケーションは、ライブラリの作成者が <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性を使用して具体的に許可しない限り、共有マネージド ライブラリを呼び出せません。 そのため、アプリケーションの作成者は、ライブラリによっては部分的に信頼されたコンテキストから使用できないことを認識する必要があります。 既定では、すべてのコードで実行する部分的に信頼された[サンド ボックス](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)ではありません。 完全信頼アセンブリの一覧が部分的に信頼されているとします。 部分的に信頼されたコンテキストからコードを実行する、または部分的に信頼されたコードによってコードが呼び出されることはないと考えられる場合は、このセクションの情報を考慮する必要はありません。 ただし、部分的に信頼されたコードと対話する必要があるコード、または部分的に信頼されたコンテキストから操作するコードを記述する場合は、次の要因を考慮する必要があります。  
  
-   ライブラリは、複数のアプリケーションで共有するために、厳密な名前で署名する必要があります。 厳密な名前を使用すると、コードをグローバル アセンブリ キャッシュに配置したり、サンドボックス化する <xref:System.AppDomain> の完全信頼一覧に追加したりできます。また、コンシューマーは、実際にあなたが発信する特定のモバイル コードを確認することができます。  
  
-   既定では、厳密な名前[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md)共有ライブラリを暗黙的な実行[LinkDemand](../../../docs/framework/misc/link-demands.md)完全でライブラリの作成者が何もすることを自動的に信頼します。  
  
-   呼び出し元に完全な信頼がないにもかかわらず、このようなライブラリを呼び出そうとする場合、ランタイムは <xref:System.Security.SecurityException> をスローします。これにより、呼び出し元はライブラリにリンクできなくなります。  
  
-   自動を無効にするには**LinkDemand**からスローされる例外を防ぐため、配置することができます、 **AllowPartiallyTrustedCallersAttribute**共有アセンブリのスコープに属性ライブラリです。 この属性により、部分的に信頼されたマネージド コードからライブラリを呼び出すことができます。  
  
-   それでも、この属性を持つライブラリへのアクセスが許可されている部分的に信頼されたコードは、<xref:System.AppDomain> が定義する追加の制約を受けます。  
  
-   部分的に信頼されたコードがないライブラリを呼び出すことのプログラムによる方法はありません、 **AllowPartiallyTrustedCallersAttribute**属性。  
  
 特定のアプリケーションをプライベートなライブラリは、厳密な名前を必要としない、または**AllowPartiallyTrustedCallersAttribute**属性し、悪意のあるコード、アプリケーションの外部から参照できません。 このようなコードは、部分的に信頼されたモバイル コードの意図的または意図的でない誤使用から保護されています。開発者は追加で何かをする必要はありません。  
  
 次の種類のコードについて、部分的に信頼されたコードによる使用を明示的に有効にすることを検討してください。  
  
-   セキュリティの脆弱性を入念にテストされているし、で説明されているガイドラインに準拠しているがコードを[安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)します。  
  
-   部分的に信頼されたシナリオ用に特に記述された厳密な名前のコード ライブラリ。  
  
-   インターネットからダウンロードしたコードによって呼び出される、厳密な名前で署名された (部分的に信頼された、または完全に信頼された) すべてのコンポーネント。   
  
> [!NOTE]
>  .NET Framework クラス ライブラリのいくつかのクラスにはありません、 **AllowPartiallyTrustedCallersAttribute**属性し、部分的に信頼されたコードから呼び出すことはできません。  
  
## <a name="see-also"></a>関連項目

- [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)
