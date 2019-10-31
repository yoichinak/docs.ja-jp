---
title: '方法 : イメージ メタデータを読み取る'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: cd3b636f8f0058d4a8eacc656f95d5f46b8967e2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040747"
---
# <a name="how-to-read-image-metadata"></a>方法 : イメージ メタデータを読み取る

一部のイメージファイルには、イメージの機能を確認するために読み取ることができるメタデータが含まれています。 たとえば、デジタル写真には、イメージのキャプチャに使用されるカメラのメーカーとモデルを決定するために読み取ることができるメタデータが含まれている場合があります。 GDI + を使用すると、既存のメタデータを読み取ることができます。また、イメージファイルに新しいメタデータを書き込むこともできます。

GDI + は、メタデータの個々の部分を <xref:System.Drawing.Imaging.PropertyItem> オブジェクトに格納します。 <xref:System.Drawing.Image> オブジェクトの <xref:System.Drawing.Image.PropertyItems%2A> プロパティを読み取って、ファイルからすべてのメタデータを取得できます。 <xref:System.Drawing.Image.PropertyItems%2A> プロパティは、<xref:System.Drawing.Imaging.PropertyItem> オブジェクトの配列を返します。

<xref:System.Drawing.Imaging.PropertyItem> オブジェクトには、`Id`、`Value`、`Len`、および `Type`の4つのプロパティがあります。

## <a name="id"></a>ID

メタデータ項目を識別するタグ。 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> に割り当てることができる値を次の表に示します。

|16進数値|説明|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|イメージのタイトル<br /><br /> 装置の製造元<br /><br /> 装置モデル<br /><br /> ExifDTOriginal<br /><br /> Exif 公開時間<br /><br /> 輝度テーブル<br /><br /> クロミナンステーブル|

## <a name="value"></a>[値]

値の配列。 値の形式は、<xref:System.Drawing.Imaging.PropertyItem.Type%2A> プロパティによって決まります。

## <a name="len"></a>Len

<xref:System.Drawing.Imaging.PropertyItem.Value%2A> プロパティが指す値の配列の長さ (バイト単位)。

## <a name="type"></a>[種類]

`Value` プロパティが指す配列内の値のデータ型。 `Type` プロパティ値によって示される形式を次の表に示します。

|数値|説明|
|-------------------|-----------------|
|1|`Byte`。|
|2|ASCII としてエンコードされた `Byte` オブジェクトの配列。|
|3|16ビット整数|
|4|32ビット整数|
|5|有理数を表す2つの `Byte` オブジェクトの配列|
|6|未使用|
|7|未定義|
|8|未使用|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>例
  
次のコード例では、ファイル `FakePhoto.jpg`内の7つのメタデータを読み取り、表示します。 一覧の2番目の (インデックス 1) プロパティ項目には <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (装置の製造元) と <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII エンコードされたバイト配列) があります。 このコード例では、そのプロパティ項目の値を表示します。

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

このコードでは、次のような出力が生成されます。

```output
 Property Item 0
  
 id: 0x320
  
 type: 2
 
 length: 16 bytes 
  
 Property Item 1
  
 id: 0x10f
  
 type: 2 
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a>コードのコンパイル

前の例は、Windows フォームで使用するように設計されています。また、<xref:System.Windows.Forms.Control.Paint> イベントハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e`が必要です。 フォームの <xref:System.Windows.Forms.Control.Paint> イベントを処理し、このコードを描画イベントハンドラーに貼り付けます。 `FakePhoto.jpg` をシステム上で有効なイメージ名とパスに置き換え、`System.Drawing.Imaging` 名前空間をインポートする必要があります。

## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
