---
title: PutInstanceWmi 関数 (アンマネージ API リファレンス)
description: PutInstanceWmi 関数は、既存のクラスのインスタンスを作成または更新します。
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798374"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi 関数

既存のクラスのインスタンスが作成または更新されます。 インスタンスは、WMI リポジトリに書き込まれます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>パラメーター

`pInst`\
から書き込むインスタンスへのポインター。

`lFlags`\
からこの関数の動作に影響を与えるフラグの組み合わせ。 次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 設定した場合、WMI は、**修正**されたフレーバーを持つ修飾子を格納しません。 <br> 設定されていない場合は、このオブジェクトがローカライズされていないと見なされ、すべての修飾子がこのインスタンスと共に格納されます。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | インスタンスが存在しない場合は作成し、既に存在する場合は上書きします。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | インスタンスを更新します。 呼び出しを成功させるには、インスタンスが存在している必要があります。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | インスタンスを作成します。 インスタンスが既に存在する場合、呼び出しは失敗します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | このフラグにより、半同期呼び出しが発生します。 |

`pCtx`\
から通常、この値は`null`です。 それ以外の場合は、要求されたクラスを提供しているプロバイダーが使用できる[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)インスタンスへのポインターです。

`ppCallResult`\
入出力の`null`場合、このパラメーターは使用されません。 に`lFlags`が`WBEM_FLAG_RETURN_IMMEDIATELY`含まれている場合、 `WBEM_S_NO_ERROR`関数はを使用してすぐにを返します。 パラメーター `ppCallResult`は、新しい[IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult)オブジェクトへのポインターを受け取ります。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 指定されたクラスのインスタンスを更新するためのアクセス許可がユーザーにありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 特定できないエラーが発生しました。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | このインスタンスをサポートしているクラスが無効です。 |
| `WBEM_E_ILLEGAL_NULL` | 0x80048 | は、**インデックス付き**または**Not_Null**修飾子に`null`よってマークされたプロパティなど、ではできないプロパティに対して指定されました。`null` |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | 指定されたインスタンスは無効です。 (たとえば、クラスを`PutInstanceWmi`使用してを呼び出すと、この値が返されます)。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが有効ではありません。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`フラグが指定されましたが、インスタンスは既に存在します。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`はで`lFlags`指定されましたが、インスタンスが存在しません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するために必要なメモリが不足しています。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI が停止し、再起動されたことがあります。 [Connectserverwmi](connectserverwmi.md)を再度呼び出します。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと WMI の間のリモートプロシージャコール (RPC) リンクが失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。 |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemServices::P utInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance)メソッドの呼び出しをラップします。

関数`PutInstanceWmi`では、インスタンスの作成と、既存のクラスのインスタンスの更新のみがサポートされます。  `pCtx`パラメーターの設定方法によっては、インスタンスの一部またはすべてのプロパティが更新されます。

によってポイントされる`pInst`インスタンスがサブクラスに属している場合、Windows Management は、サブクラスの派生元であるクラスを担当するすべてのプロバイダーを呼び出します。 元`PutInstanceWmi`の要求を成功させるには、これらのプロバイダーのすべてが成功する必要があります。 階層内の最上位のクラスをサポートするプロバイダーが最初に呼び出されます。 呼び出し順序は最上位クラスのサブクラスから続行され、Windows Management がによって`pInst`ポイントされたインスタンスを所有するクラスのプロバイダーに到達するまで、上から下に進みます。
Windows Management では、インスタンスのどの子クラスに対してもプロバイダーは呼び出されません。

クラス階層に属しているインスタンスをアプリケーションで更新する必要がある`pInst`場合、パラメーターは、変更するプロパティを含むインスタンスを指す必要があります。 つまり、 **Classb**に属するターゲットインスタンスを考えてみましょう。 **Classb**インスタンスは**classb**から派生し、 **Classb**はプロパティ**propa**を定義します。 アプリケーションで**classb**インスタンスの**propa**の値を変更する場合は、 **classb**のインスタンスではなく`pInst` 、そのインスタンスに設定する必要があります。

抽象`PutInstanceWmi`クラスのインスタンスでを呼び出すことはできません。

関数呼び出しが失敗した場合は、 [GetErrorInfo](geterrorinfo.md)関数を呼び出して追加のエラー情報を取得できます。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
