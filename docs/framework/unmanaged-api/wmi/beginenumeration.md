---
title: BeginEnumeration 関数 (アンマネージ API リファレンス)
description: BeginEnumeration 関数は、列挙子を列挙体の先頭にリセットします。
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de36650aa2b206b5e9734b38c6067a3a79de610c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798784"
---
# <a name="beginenumeration-function"></a>BeginEnumeration 関数
列挙子を列挙体の先頭にリセットします。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`\
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`lEnumFlags`\
から列挙に含まれるプロパティを制御する、「[解説](#remarks)」で説明されているフラグまたは値のビットごとの組み合わせ。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | の`lEnumFlags`フラグの組み合わせが無効であるか、無効な引数が指定されました。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | への2回`BeginEnumeration`目の呼び出しは、の間[`EndEnumeration`](endenumeration.md)の呼び出しなしで行われました。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するために必要なメモリが不足しています。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject:: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)メソッドの呼び出しをラップします。

`lEnumFlags`引数として渡すことができるフラグは、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。  各グループのフラグは、他のグループのフラグと組み合わせることができます。 ただし、同じグループのフラグは相互に排他的です。 

**グループ1**

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | キーのみを構成するプロパティを含めます。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | オブジェクト参照のみのプロパティを含めます。 |

**グループ2**

定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 列挙体をシステムプロパティのみに制限します。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | ローカルプロパティと伝達されたプロパティを含めますが、列挙からシステムプロパティを除外します。 |

クラスの場合:

定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | 列挙型をクラス定義でオーバーライドされたプロパティに限定します。 |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | 列挙体を、現在のクラス定義でオーバーライドされたプロパティと、クラスで定義されている新しいプロパティに限定します。 |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `lEnumFlags` また`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`はが設定されているかどうかを確認するために、値に対して適用するマスク (フラグではなく)。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 列挙体は、クラス自体で定義または変更されたプロパティに限定します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 列挙型を基底クラスから継承されたプロパティに限定します。 |

インスタンスの場合:

定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 列挙体は、クラス自体で定義または変更されたプロパティに限定します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 列挙型を基底クラスから継承されたプロパティに限定します。 |

## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
