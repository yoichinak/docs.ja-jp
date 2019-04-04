---
title: FormatFromRawValue 関数 (アンマネージ API リファレンス)
description: FormatFromRawValue 関数では、生のパフォーマンス データを指定された形式に変換します。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a84b03c85cc1332c07ffbaf53187b7f01d0236
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262467"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue 関数
1 つの生のパフォーマンス データ値が指定した形式に変換されます。この形式変換が時間ベースである場合は、2 つの生のパフォーマンス データ値が変換されます。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a>パラメーター

`dwCounterType`\
[in]カウンターの型。 カウンターの種類の一覧は、[WMI パフォーマンス カウンターの種類](/windows/desktop/WmiSdk/wmi-performance-counter-types)を参照してください。 `dwCounterType` 以外の任意のカウンター タイプ`PERF_LARGE_RAW_FRACTION`と`PERF_LARGE_RAW_BASE`します。 

`dwFormat`\
[in]生のパフォーマンス データを変換先の形式。 次の値のいずれかを指定できます。

|定数  |値  |説明 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 倍精度浮動小数点値として計算される値を返します。 | 
| `PDH_FMT_LARGE` | 0x00000400 | 計算される値を 64 ビット整数として返します。 |
| `PDH_FMT_LONG` | 0x00000100 | 計算される値を 32 ビット整数として返します。 |

次のスケーリング フラグのいずれかの論理和前の値のいずれかのことができます。

|定数  |値  |説明 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | カウンターのスケール ファクターは適用されません。 |
| `PDH_FMT_1000` | 0x00002000 | 1000 で最終的な値を乗算します。 | 

`pTimeBase`\
[in]形式の変換に必要な場合、時間ベースへのポインター。 時間ベースの情報は、形式変換の必要はありません、このパラメーターの値は無視されます。

`pRawValue1`\ [in] へのポインターを[ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter)生のパフォーマンス値を表す構造体です。

`pRawValue2`\
[in]ポインターを[ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) 2 番目の生のパフォーマンス値を表す構造体です。 2 番目の生のパフォーマンス値が必要でない場合、このパラメーターがあります`null`します。

`pFmtValue`\
[out]ポインターを[ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue)を書式設定されたパフォーマンスの値を受け取る構造体。

## <a name="return-value"></a>戻り値

この関数では、次の値が返されます。

|定数  |値  |説明  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 関数呼び出しは成功します。 |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 必須の引数が不足しているか、正しくありません。 | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | ハンドルが有効な PDH オブジェクトです。 |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))関数。

## <a name="requirements"></a>必要条件

 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

 **ライブラリ:** どちら

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
