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
ms.openlocfilehash: ba11eed316e227ceae4cb5acecb2b081fa8868f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705533"
---
# <a name="configuring-cryptography-classes"></a>暗号化クラスの設定
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]コンピューターの管理者は、既定の暗号アルゴリズムと、.NET Framework と適切に記述されたアプリケーションを使用するアルゴリズムの実装を構成します。  たとえば、暗号アルゴリズムの独自の実装を持つエンタープライズは、その実装に出荷された実装ではなく既定、[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]します。 暗号化を使用するマネージ アプリケーションは、特定の実装にバインドするように常に選択できますが、crypto の構成システムを使用して暗号化オブジェクトを作成することをお勧めします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [暗号化クラスへのアルゴリズム名の割り当て](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 暗号化クラスに、アルゴリズム名をマップする方法について説明します。  
  
 [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 暗号化アルゴリズムにオブジェクト識別子をマップする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)  
 によって提供されるサービスの暗号化の概要、[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]します。  
  
 [暗号化設定スキーマ](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。
