---
title: コントラクト
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868429"
---
# <a name="contract"></a>コントラクト
コントラクト  
  
## <a name="syntax"></a>構文  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>メソッド  
 Contract クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>Properties  
 Contract クラスには、次のプロパティがあります。  
  
### <a name="appdomainid"></a>AppDomainId  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用です。  
  
 コントラクトをホストする appdomain の appdomain ID。  
  
### <a name="behaviors"></a>ビヘイビアー  
 データの種類:動作の配列  
  
 アクセスの種類:読み取り専用です。  
  
 このコントラクトに関連付けられている動作。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 WSDL でのコントラクトの名前。  
  
### <a name="namespace"></a>名前空間  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 WSDL での `portType` 要素の名前空間。  
  
### <a name="operations"></a>操作  
 データの種類:Operation 配列  
  
 アクセスの種類:読み取り専用です。  
  
 このコントラクトの操作。  
  
### <a name="processid"></a>ProcessId  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用です。  
  
 コントラクトをホストするプロセスのプロセス ID。  
  
### <a name="ref"></a>ref  
 データの種類:コントラクト  
  
 アクセスの種類:読み取り専用です。  
  
 コントラクトが双方向コントラクトのときのコールバックの型。  
  
### <a name="sessionmode"></a>SessionMode  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 コントラクトでチャネル セッションを使用するために、このコントラクトに関連付けられたバインディングが必要かどうかを示します。  
  
### <a name="type"></a>種類  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 コントラクトの型。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ContractDescription>
