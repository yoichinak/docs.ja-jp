---
title: '方法: イメージのメタデータの読み取り'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: eba21519e6ea6cf4a2a412750fd305d7af620c1b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720793"
---
# <a name="how-to-read-image-metadata"></a>方法: イメージのメタデータの読み取り
一部のイメージ ファイルには、イメージの機能を読み取ることができるメタデータが含まれます。 たとえば、デジタル写真には、製造元とイメージをキャプチャするために使用するカメラのモデルを決定する読み取り可能なメタデータが含まれます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、既存のメタデータを読み取ることができ、イメージ ファイルに新しいメタデータを記述することもできます。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] メタデータ内の個々 の部分を格納、<xref:System.Drawing.Imaging.PropertyItem>オブジェクト。 読み取ることができます、<xref:System.Drawing.Image.PropertyItems%2A>のプロパティ、<xref:System.Drawing.Image>ファイルからすべてのメタデータを取得するオブジェクト。 <xref:System.Drawing.Image.PropertyItems%2A>プロパティの配列を返します<xref:System.Drawing.Imaging.PropertyItem>オブジェクト。  
  
 A<xref:System.Drawing.Imaging.PropertyItem>オブジェクトが次の 4 つのプロパティ: `Id`、 `Value`、 `Len`、および`Type`します。  
  
## <a name="id"></a>ID  
 メタデータ項目を識別するタグ。 いくつかの値を割り当てることができる<xref:System.Drawing.Imaging.PropertyItem.Id%2A>次の表に表示されます。  
  
|16 進数の値|説明|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|イメージのタイトル<br /><br /> 機器の製造元<br /><br /> 機器のモデル<br /><br /> ExifDTOriginal<br /><br /> Exif の露出時間<br /><br /> 輝度テーブル<br /><br /> クロミナンス テーブル|  
  
## <a name="value"></a>[値]  
 値の配列。 値の形式が定め、<xref:System.Drawing.Imaging.PropertyItem.Type%2A>プロパティ。  
  
## <a name="len"></a>Len  
 によって示される値の配列の長さ (バイト単位) で、<xref:System.Drawing.Imaging.PropertyItem.Value%2A>プロパティ。  
  
## <a name="type"></a>型  
 指す配列内の値のデータ型、`Value`プロパティ。 によって示される形式、`Type`プロパティの値が次の表に示すように  
  
|数値|説明|  
|-------------------|-----------------|  
|1|
  `Byte`。|  
|2|配列の`Byte`ascii 形式でエンコードされたオブジェクト|  
|3|16 ビット整数|  
|4|32 ビット整数|  
|5|2 つの配列`Byte`有理数を表すオブジェクト|  
|6|未使用|  
|7|未定義|  
|8|未使用|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例を読み取って、ファイルの 7 つのメタデータを表示します。`FakePhoto.jpg`します。 一覧には、2 つ目の (インデックス 1) プロパティ項目には<xref:System.Drawing.Imaging.PropertyItem.Id%2A>0x010F (メーカー) と<xref:System.Drawing.Imaging.PropertyItem.Type%2A>2 (ASCII でエンコードされたバイト配列)。 コード例では、そのプロパティの項目の値が表示されます。  
  
 コードには、次のような出力が生成されます。  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a>コード  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 フォームの処理<xref:System.Windows.Forms.Control.Paint>イベント paint イベント ハンドラーに次のコードを貼り付けます。 置き換える必要があります`FakePhoto.jpg`イメージ名と、システムとインポートの有効なパス、`System.Drawing.Imaging`名前空間。  
  
## <a name="see-also"></a>関連項目
- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
