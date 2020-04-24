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
ms.openlocfilehash: 61291a07639c3f92a05f78dff49f6b20f1aee77e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645714"
---
# <a name="using-libraries-from-partially-trusted-code"></a>部分信頼コードからのライブラリの使用
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> このトピックでは、厳密な名前付きアセンブリの動作について説明し、[レベル 1](security-transparent-code-level-1.md)のアセンブリにのみ適用されます。 NET Framework 4 以降[のセキュリティ透過的コードレベル 2](security-transparent-code-level-2.md)アセンブリは、厳密な名前の影響を受けません。 セキュリティ システムの変更の詳細については、「[セキュリティの変更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)」を参照してください。  
  
 ホストまたはサンドボックスから不完全な信頼を受けているアプリケーションは、ライブラリの作成者が <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性を使用して具体的に許可しない限り、共有マネージド ライブラリを呼び出せません。 そのため、アプリケーションの作成者は、ライブラリによっては部分的に信頼されたコンテキストから使用できないことを認識する必要があります。 既定では、部分信頼[サンドボックス](how-to-run-partially-trusted-code-in-a-sandbox.md)で実行され、完全信頼アセンブリの一覧に含まれていないすべてのコードは、部分的に信頼されます。 部分的に信頼されたコンテキストからコードを実行する、または部分的に信頼されたコードによってコードが呼び出されることはないと考えられる場合は、このセクションの情報を考慮する必要はありません。 ただし、部分的に信頼されたコードと対話する必要があるコード、または部分的に信頼されたコンテキストから操作するコードを記述する場合は、次の要因を考慮する必要があります。  
  
- ライブラリは、複数のアプリケーションで共有するために、厳密な名前で署名する必要があります。 厳密な名前を使用すると、コードをグローバル アセンブリ キャッシュに配置したり、サンドボックス化する <xref:System.AppDomain> の完全信頼一覧に追加したりできます。また、コンシューマーは、実際にあなたが発信する特定のモバイル コードを確認することができます。  
  
- 既定では、厳密な名前の[レベル 1](security-transparent-code-level-1.md)共有ライブラリは、ライブラリ作成者が何もしなくても、完全信頼に対して暗黙的な[LinkDemand](link-demands.md)を自動的に実行します。  
  
- 呼び出し元に完全な信頼がないにもかかわらず、このようなライブラリを呼び出そうとする場合、ランタイムは <xref:System.Security.SecurityException> をスローします。これにより、呼び出し元はライブラリにリンクできなくなります。  
  
- 自動**リンク要求**を無効にし、例外がスローされないようにするには、共有ライブラリのアセンブリ スコープに**属性**を配置します。 この属性により、部分的に信頼されたマネージド コードからライブラリを呼び出すことができます。  
  
- それでも、この属性を持つライブラリへのアクセスが許可されている部分的に信頼されたコードは、<xref:System.AppDomain> が定義する追加の制約を受けます。  
  
- 部分的に信頼されたコードが **、属性**を持たないライブラリを呼び出すプログラム的な方法はありません。  
  
 特定のアプリケーションにプライベートなライブラリは、厳密な名前または**AllowPartiallyTrustedCallersAttribute 属性を**必要とせず、アプリケーションの外部で悪意のあるコードによって参照することはできません。 このようなコードは、部分的に信頼されたモバイル コードの意図的または意図的でない誤使用から保護されています。開発者は追加で何かをする必要はありません。  
  
 次の種類のコードについて、部分的に信頼されたコードによる使用を明示的に有効にすることを検討してください。  
  
- セキュリティの脆弱性について熱心にテストされ、「[コードのセキュリティ](../../standard/security/secure-coding-guidelines.md)保護ガイドライン」に記載されているガイドラインに準拠しているコード。  
  
- 部分的に信頼されたシナリオ用に特に記述された厳密な名前のコード ライブラリ。  
  
- インターネットからダウンロードしたコードによって呼び出される、厳密な名前で署名された (部分的に信頼された、または完全に信頼された) すべてのコンポーネント。   
  
> [!NOTE]
> .NET Framework クラス ライブラリ内の一部のクラスには **、属性が含**まれていないため、部分信頼コードから呼び出すことはできません。  
  
## <a name="see-also"></a>関連項目

- [コード アクセス セキュリティ](code-access-security.md)
