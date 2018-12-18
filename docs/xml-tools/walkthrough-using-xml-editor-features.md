---
title: 'İzlenecek Yol: XML Düzenleyicisi Özelliklerini Kullanma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afda2968ece2a18b7abdc2c4c35e4353206cbe42
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693831"
---
# <a name="walkthrough-use-xml-editor-features"></a>İzlenecek yol: Kullanmak XML Düzenleyicisi özellikleri

Bu izlenecek adımları yeni bir XML belgesi nasıl oluşturacağınızı gösterir. İzlenecek yol da XML yazmak için değerli kılan özelliklerin bir XML Düzenleyicisi'nin kullanır.

> [!NOTE]
> İzlenecek yol başlatmadan önce kaydetmek *hireDate.xsd* (aşağıda bu konuya da dahil) dosyasını yerel bilgisayarınıza.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Yeni bir XML dosyası oluşturmak ve bir XML şeması ile ilişkilendirmek için

1.  Üzerinde **dosya** menüsündeki **yeni**, tıklatıp **dosya**.

2.  Seçin **XML dosyası** içinde **şablonları** bölmesinde ve tıklatın **açık**.

     Yeni bir dosya Düzenleyicisi'nde açılır. Varsayılan XML bildirimi dosyayı içeren `<?xml version="1.0" encoding="utf-8">`.

3.  Belge Özellikleri penceresinde Gözat düğmesine (**...** ) üzerinde **şemaları** alan.

     **XSD şemaları** iletişim kutusu görüntülenir.

4.  **Ekle**'yi tıklatın.

     **Açık XSD şema** iletişim kutusu görüntülenir.

5.  Seçin *hireDate.xsd* dosya ve tıklayın **açık**.

6.  **Tamam**'ı tıklatın.

     XML Şeması sunulmuştur XML belgesi ile ilişkilendirilmiş. XML Şeması belgesi doğrulamak için kullanılır. Bu ayrıca, IntelliSense tarafından geçerli öğeleri üye listesini doldurmak için kullanılır.

## <a name="to-add-data"></a>Veri eklemek için

1.  Tür `<` Düzenleyicisi bölmesinde.

     Üye listesi olası öğeleri görüntüler:

    -   **!--** bir yorum ekleyin.

    -   **! DOCTYPE** bir belge türü eklemek için.

    -   **?** bir işlem yönergesi eklemek için.

    -   **çalışan** kök öğesi eklemek için.

2.  Seçin **<!--** açıklama düğümü ve tuşuna eklemek için **Enter**.

     Düzenleyici, açıklama bitiş etiketi ekler ve imleci başlangıç ve bitiş yorum etiketleri arasına yerleştirir.

3.  Yazın **Test XML dosyası**.

4.  Yeni bir satıra yazın `<`seçip **çalışan** üye listesinden.

     Düzenleyici bir XML öğesi ekler `<employee`. Bu noktada öznitelikleri öğesine ekleyebilir veya yazarak başlangıç etiketi kapatabilirsiniz `>`.

5.  Tür `>` etiket kapatın.

6.  Düzenleyici bitiş etiketi ekler. Bitiş etiketi bir doğrulama hatası gösteren dalgalı alt çizgi ile eklenir. **Araç ipucu** iletisini görüntüler: **içeriği eksik 'çalışanı' öğesine sahip. 'ID' beklenen**.

7.  Tür `<` seçip **kimliği** üye listesinden. Yazın `>`.

     Düzenleyici XML öğesi ekler `<ID></ID>`ve imleci kimliği başlattıktan sonra etiketi yerleştirir.

8.  Tür **abc**.

     **Abc** metin dalgalı alt çizgiyle sahiptir. **Araç ipucu** iletisini görüntüler: **'ID' öğesi kendi veri türüne göre geçersiz bir değere sahip**.

9. Kimliği öğeyi sağ tıklatıp **Tanıma Git**.

     Düzenleyici açılır *hireDate.xsd* yeni bir belge penceresi dosyasında ve imleci kimliği şema öğesi tanımını yerleştirir.

10. XML dosyasına dönmek ve Değiştir **abc** metinle **123**.

     Dalgalı alt çizgi ve **araç ipucu** altındaki kimliği öğesi değeri temizlenir. **Araç ipucu** için çalışan bitiş etiketi şimdi iletisini görüntüler: **içeriği eksik 'çalışanı' öğesine sahip. Beklenen 'işe alma-date'**.

11. İmleci kimliği Bitiş etiketinden sonra yerleştirin, yazın `<`seçin **işe alma tarihi** üye listesine ve ardından türü `>`.

     Düzenleyici XML öğesi ekler `<hire-date></hire-date>`ve işe alma tarihi başlattıktan sonra etiketi imleci yerleştirir.

12. Yazın **2003-01-10** işe alma tarihi değeri.

## <a name="to-format-the-xml-document"></a>XML belgesi biçimlendirmek için

- Seçin **belgeyi Biçimlendir** XML Düzenleyicisi araç çubuğu düğmesinden.

    XML belgesi biçimlendirilir.

## <a name="to-save-the-xml-document"></a>XML belgesi kaydetmek için

1.  Gelen **dosya** menüsünde, select **Kaydet**.

     **Dosyasını Farklı Kaydet** iletişim kutusu görüntülenir. Varsayılan dosya adı *'XMLFile1'*.

2.  XML belgesi için konum ve dosya adı girin ve tıklayın **kaydetmek**.

## <a name="hiredatexsd-file"></a>hireDate.xsd dosyası
 Aşağıdaki şema dosyası izlenecek yol tarafından kullanılır.

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)