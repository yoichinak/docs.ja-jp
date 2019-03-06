---
title: Get 関数 (アンマネージ API リファレンス)
description: Get 関数には、指定されたプロパティ値を取得します。
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7534d760f902f80d42c6c20c57a34d52012997a7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369657"
---
# <a name="get-function"></a>Get 関数

存在する場合は、指定されたプロパティ値を取得します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`wszName`\
[in]プロパティの名前。

`lFlags`\
[in] 予約されています。 このパラメーターは、0 を指定する必要があります。

`pVal`\
[out]関数が正常に返された場合の値が含まれています、`wszName`プロパティ。 `pval`引数には、正しい型および修飾子の値が割り当てられています。

`pvtType`\
[out]関数が正常に返された場合は、 [CIM 型の定数](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration)プロパティの型を示します。 その値が指定できますも`null`します。 

`plFlavor`\
[out]関数が正常に返された場合は、プロパティのパブリッシュ元に関する情報を受け取ります。 その値を指定できます`null`、またはいずれかで定義されている次の WBEM_FLAVOR_TYPE 定数、 *WbemCli.h*ヘッダー ファイル。 

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | プロパティは、標準のシステム プロパティです。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | クラス。プロパティは、親クラスから継承されます。 <br> インスタンス。プロパティを親クラスから継承したときに変更されていないインスタンスがします。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | クラス。プロパティは、派生クラスに属しています。 <br> インスタンス。インスタンスでプロパティを変更します。つまり、値が指定されましたまたは修飾子が追加または変更します。 |

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが無効です。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定したプロパティが見つかりませんでした。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)メソッド。

`Get`関数では、システムのプロパティを返すこともできます。

`pVal`引数には、正しい型および修飾子と COM の値が割り当てられている[VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)関数

## <a name="requirements"></a>必要条件

 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** WMINet_Utils.idl

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)