---
title: Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 593bb95e45ecdbda14eba49425ce5db08369e6cf
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783694"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)

Kullanım **AdvancedCompiler ayarları** iletişim kutusunun **Proje Tasarımcısı** Proje Gelişmiş yapı yapılandırması özelliklerini belirtmek için. Bu iletişim kutusu, yalnızca Visual Basic projeleri için geçerlidir.

## <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1.  İçinde **Çözüm Gezgini**, bir proje düğümü seçin (değil **çözüm** düğümü).

2.  Üzerinde **proje** menüsünü tıklatın **özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklayın **derleme** sekmesi.

3.  Üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)seçin **yapılandırma** ve **Platform**. Basitleştirilmiş yapı yapılandırmaları **yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için [nasıl yapılır: ayarlama hata ayıklama ve dağıtım yapılandırmalarını](../../debugger/how-to-set-debug-and-release-configurations.md).

4.  Tıklayın **Gelişmiş derleme seçenekleri**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>En iyi duruma getirme

 Bazı durumlarda bir program dosyası küçültmek, bir program daha hızlı çalıştırın veya derleme sürecinize hız yapmadan en iyi duruma getirme aşağıdaki seçenekleri belirtin.

**Tamsayı taşması denetimlerini Kaldır**

Bu onay kutusu, tamsayı taşma denetimini etkinleştirmek için varsayılan olarak işaretli değildir. Tamsayı taşma denetimini kaldırmak için bu onay kutusunu seçin. Bu onay kutusunu seçerseniz, tamsayı hesaplamalar daha hızlı olabilir. Ancak, taşma denetimi ve veri türü kapasiteler taşma kaldırırsanız, hatalı sonuçlar ortaya çıkan bir hata depolanabilir.

Taşma koşullar denetlenir ve bir tamsayı işlem taşıyor, bir <xref:System.OverflowException> özel durumu oluşturulur. Tamsayı işlemi taşıyor, taşma koşullar denetlenir değil, bir özel durum yok.

**Eniyileştirmeleri etkinleştir**

Bu onay kutusu, derleyici iyileştirmeleri devre dışı bırakmak için varsayılan olarak işaretli değildir. Derleyici iyileştirmeleri etkinleştirmek için bu onay kutusunu seçin. Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli olun. En iyi duruma getirme, kodu yeniden çıkış dosyasında nedeni, ancak derleyici iyileştirmeleri hata ayıklamayı zorlaştırabilir.

 **DLL temel adresi**

 Bu metin kutusunda varsayılan DLL temel adresi onaltılık biçiminde görüntüler. Sınıf kitaplığı ve Denetim Kitaplığı projeleri DLL'si oluşturulurken kullanılacak temel adresini belirtmek için bu metin kutusunu kullanabilirsiniz.

 **Hata ayıklama bilgileri üret**

 Seçin **hiçbiri**, **tam**, veya **yalnızca pdb** listeden. **Hiçbiri** hata ayıklama bilgisi oluşturulacağını belirtir. **Tam** tam hata ayıklama bilgilerini oluşturulan gerektiğini belirtir ve **yalnızca pdb** hata ayıklama bilgileri yalnızca PDB oluşturulacağını belirtir. Bu seçenek için varsayılan değerdir **tam**.

## <a name="compilation-constants"></a>Derleme sabitleri

Koşullu derleme sabitleri sahip efekt, kullanmanın benzer bir [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) önişlemci yönergesi bir kaynak dosya, tanımlı sabitler herkese açık ve projedeki tüm dosyalar için geçerlidir. Koşullu derleme sabitleri ile birlikte kullanabileceğiniz [#If... Then... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) yönergesi, kaynak dosyaları koşullu olarak derleyebilirsiniz. Bkz: [koşullu derleme](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **DEBUG sabitini tanımlayın**

 Varsayılan olarak, bir hata ayıklama sabit ayarlanması belirterek bu onay kutusu seçilidir.

 **TRACE sabitini tanımlayın**

 Varsayılan olarak, TRACE sabitini ayarlanması belirterek bu onay kutusu seçilidir.

 **Özel sabitleri**

 Bu metin kutusunda, uygulamanızın herhangi özel bir sabit girin. Girişleri bu formu kullanarak virgülle ayrılmış: **Name1 "Value1", Name2 = "Value2", Name3 = "Value3"**.

## <a name="other-settings"></a>Diğer ayarlar

**Serileştirme bütünleştirilmiş kodları üret**

Bu ayar, derleyicinin XML serileştirme derlemeleri oluşturacak olup olmadığını belirtir. Serileştirme derlemeleri başlatma performansını geliştirebilir <xref:System.Xml.Serialization.XmlSerializer> kodunuzda türleri serileştirmek için bu sınıfı kullandıysanız. Bu seçenek için varsayılan değerdir **otomatik**. **Otomatik** yalnızca kullandıysanız, serileştirme derlemelerinin oluşturulacağını belirten <xref:System.Xml.Serialization.XmlSerializer> kodunuzdaki XML kodlama. **Kapalı** serileştirme derlemelerinin hiçbir zaman, kodunuzun kullanıp bağımsız olarak oluşturulmamasını belirtir <xref:System.Xml.Serialization.XmlSerializer>. **Üzerinde** serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme derlemeleri yeniden adlandırılır `TypeName`. XmlSerializers.dll.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)