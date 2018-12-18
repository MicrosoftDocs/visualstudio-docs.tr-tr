---
title: Gelişmiş Seçenekler, metin düzenleyici, Basic (VB)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b15617dce090a3aacde71ad48bf4984f5efbcac4
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218931"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Gelişmiş Seçenekler, metin düzenleyici, temel (Visual Basic)
**VB belirli** özellik sayfasında **temel** klasörü **metin düzenleyici** klasörü **seçenekleri** (**araçları** menüsü) iletişim kutusu aşağıdaki özellikleri içerir:

 **Başvuruları ve anahtar sözcükleri vurgulamasını etkinleştirmenin**

Metin Düzenleyicisi gibi bir simgenin tüm örnekleri veya tüm yan tümcesindeki anahtar sözcüklerin vurgulayabilirsiniz `If..Then`, `While...End While`, veya `Try...Catch...Finally`. Vurgulanan başvurulara veya anahtar sözcükler tuşlarına basarak gezinebilirsiniz **Ctrl** + **Shift** + **aşağı ok** veya **Ctrl**   +  **Shift** + **yukarı ok**.

**Anahat oluşturma modunu etkinleştir**

Kod Düzenleyicisi'nde bir dosyayı açtığınızda, belge anahat modunda görüntüleyebilirsiniz. Bkz: [anahat](../../ide/outlining.md) daha fazla bilgi için. Bu seçenek belirlendiğinde, bir dosyayı açtığınızda anahat oluşturma özelliği etkinleştirilir.

**Yordam satır ayıraçlarını Göster**

Metin düzenleyici, yordamların görsel kapsamını belirtir. Bir çizgi çizilir *.vb* konumlarda projenizin kaynak dosyaları aşağıdaki tabloda listelenen:

|.Vb kaynak dosya konumu|Satır konumu örneği|
|---------------------------------|------------------------------|
|Sonra bir blok bildirimi yapısı kapatma|-Sonunda sınıfı, yapısı, modülü, arabirim veya numaralandırma<br />-Özelliği, işlev veya alt after<br />-Get ve set değil arasında bir özellikte yan tümceleri|
|Tek satır yapıları bir dizi sonra|-İçeri aktarma deyimlerini after, önce bir sınıf dosyası içinde bir tür tanımı<br />-Bir sınıftaki tüm yordamları önce tanımlanan değişkenleri after|
|Tek satır bildirimlerinden sonra (blok düzey bildirimleri)|-İçeri aktarma deyimlerini aşağıdaki deyimleri, değişken bildirimleri, olay bildirimleri, temsilci bildirimleri devralır ve DLL ifadeleri bildirme|

 **(Kodu yeniden biçimlendirme) düzgün listeleme** metin düzenleyici, uygun şekilde kodunuzu yeniden biçimlendirir. Bu seçenek belirlendiğinde, Kod Düzenleyici olur:

-   Kodunuz doğru sekme konumuna Hizala

-   Anahtar sözcükler, değişkenler ve doğru çalışması için nesneler recase

-   Eksik ekleme `Then` için bir `If...Then` deyimi

-   İşlev çağrıları için parantez ekleyin

-   Bitiş tırnak işaretleri eksik dizelere ekleme

-   Üstel gösterim yeniden biçimlendirin

-   Tarihleri yeniden biçimlendirin

**Bitiş yapılarını otomatik ekleme**

 Yazdığınızda — Örneğin, bir yordam bildirimi ilk satırını `Sub Main—`tuşuna basın **Enter**, eşleşen bir metin düzenleyicisi ekler `End Sub` satır. Benzer şekilde, eklerseniz bir [için](/dotnet/visual-basic/language-reference/statements/for-next-statement) döngüsü, metin düzenleyici ekler eşleşen `Next` deyimi. Bu seçenek belirlendiğinde, Kod Düzenleyicisi bitiş yapısı otomatik olarak ekler.

**Interface ve MustOverride üyelerinin otomatik ekleme**

İşlerseniz bir `Implements` deyimi veya bir `Inherits` ifadesi için bir sınıf, metin düzenleyici ekler prototipleri uygulanan ya da geçersiz, sırasıyla sahip üyeler için.

**Hata düzeltme önerilerini etkinleştirmek**

Metin düzenleyici, sık karşılaşılan çözümler önermek ve uygun düzeltmeyi kodunuza sonra uygulanır seçmenize olanak tanır.

## <a name="see-also"></a>Ayrıca Bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)