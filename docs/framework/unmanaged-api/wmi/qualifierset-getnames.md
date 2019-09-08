---
title: QualifierSet_GetNames 関数 (アンマネージ API リファレンス)
description: QualifierSet_GetNames 関数は、オブジェクトまたはプロパティから修飾子の名前を取得します。
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266462a5393c8e26aa2bc3f2ec8ab72d4410a431
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798296"
---
# <a name="qualifierset_getnames-function"></a>QualifierSet_GetNames 関数

現在のオブジェクトまたはプロパティから使用可能な、すべての修飾子または特定の修飾子の名前を取得します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)インスタンスへのポインター。

`lFlags`\
から列挙に含める名前を指定する、次のいずれかのフラグまたは値。

|定数  |Value  |説明  |
|---------|---------|---------|
|  | 0 | すべての修飾子の名前を返します。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 現在のプロパティまたはオブジェクトに固有の修飾子の名前のみを返します。 <br/> プロパティの場合:プロパティに固有の修飾子 (オーバーライドを含む) だけを返します。クラス定義から伝達された修飾子は返しません。 <br/> インスタンスの場合:インスタンス固有の修飾子名だけを返します。 <br/> クラスの場合:派生するクラスに固有の修飾子だけを返します。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 別のオブジェクトから伝達された修飾子の名前のみを返します。 <br/> プロパティの場合:プロパティ自体からではなく、クラス定義からこのプロパティに反映された修飾子だけを返します。 <br/> インスタンスの場合:クラス定義から伝達された修飾子だけを返します。 <br/> クラスの場合:親クラスから継承された修飾子名だけを返します。 |

`pstrNames`\
入出力要求さ`SAFEARRAY`れた名前を格納している新しい。 配列には、0個の要素を含めることができます。 エラーが発生した場合は`SAFEARRAY` 、新しいが返されません。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが有効ではありません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するために必要なメモリが不足しています。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames)メソッドの呼び出しをラップします。

修飾子名を取得したら、 [QualifierSet_Get](qualifierset-get.md)関数を呼び出すことによって、各修飾子に名前でアクセスできます。

指定されたオブジェクトが修飾子を持たない場合のエラーではないため、関数が`pstrNames`を返す`WBEM_S_NO_ERROR`場合でも、戻り時の内の文字列の数は0になることがあります。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
