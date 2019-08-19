---
title: 暗号化クラスの設定
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567339"
---
# <a name="configuring-cryptography-classes"></a>暗号化クラスの設定
Windows SDK を使用すると、コンピューター管理者は、.NET Framework および適切に記述されたアプリケーションで使用される既定の暗号化アルゴリズムおよびアルゴリズムの実装を構成できます。  たとえば、暗号化アルゴリズムを独自に実装する企業は、Windows SDK に付属する実装ではなく、その実装を既定値にすることができます。 暗号化を使用するマネージアプリケーションは、常に特定の実装に明示的にバインドすることができますが、暗号化の構成システムを使用して暗号化オブジェクトを作成することをお勧めします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [暗号化クラスへのアルゴリズム名の割り当て](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 アルゴリズム名を暗号クラスにマップする方法について説明します。  
  
 [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 オブジェクト識別子を暗号アルゴリズムにマップする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)  
 Windows SDK によって提供される暗号化サービスの概要について説明します。  
  
 [暗号化設定スキーマ](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。
