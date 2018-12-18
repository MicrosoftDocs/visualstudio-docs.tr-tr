---
title: Gelişmiş derleyici Ayarları iletişim kutusu (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd910b0e0295ca12807b96af189032ffec766429
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949831"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kullanım **AdvancedCompiler ayarları** iletişim kutusunun **Proje Tasarımcısı** Proje Gelişmiş yapı yapılandırması özelliklerini belirtmek için. Bu iletişim kutusu, yalnızca Visual Basic projeleri için geçerlidir.  
  
### <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için  
  
1. İçinde **Çözüm Gezgini**, bir proje düğümü seçin (değil **çözüm** düğümü).  
  
2. Üzerinde **proje** menüsünü tıklatın **özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklayın **derleme** sekmesi.  
  
3. Üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)seçin **yapılandırma** ve **Platform**. Basitleştirilmiş yapı yapılandırmaları **yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
4. Tıklayın **Gelişmiş derleme seçenekleri**.  
  
   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="optimizations"></a>En iyi duruma getirme  
 Bazı durumlarda bir program dosyası küçültmek, bir program daha hızlı çalıştırın veya derleme sürecinize hız yapmadan en iyi duruma getirme aşağıdaki seçenekleri belirtin.  
  
 **Tamsayı taşması denetimlerini Kaldır**  
 Varsayılan olarak, tamsayı taşma denetimini etkinleştirmek için bu onay kutusu işaretli. Tamsayı taşma denetimini kaldırmak için bu onay kutusunu seçin. Bu onay kutusunu seçerseniz, tamsayı hesaplamalar daha hızlı olabilir. Ancak, taşma denetimi ve veri türü kapasiteler taşma kaldırırsanız, hatalı sonuçlar ortaya çıkan bir hata depolanabilir.  
  
 Taşma koşullar denetlenir ve bir tamsayı işlem taşıyor, bir <xref:System.OverflowException> özel durumu oluşturulur. Tamsayı işlemi taşıyor taşma koşullar denetlenir değil, bir özel durum değil.  
  
 **Eniyileştirmeleri etkinleştir**  
 Varsayılan olarak, derleyici iyileştirmeleri devre dışı bırakmak için bu onay kutusu işaretli. Derleyici iyileştirmeleri etkinleştirmek için bu onay kutusunu seçin. Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli olun. En iyi duruma getirme, kodu yeniden çıkış dosyasında nedeni, ancak derleyici iyileştirmeleri hata ayıklamayı zorlaştırabilir.  
  
 **DLL temel adresi**  
 Bu metin kutusunda varsayılan DLL temel adresi onaltılık biçiminde görüntüler. Sınıf kitaplığı ve Denetim Kitaplığı projeleri DLL'si oluşturulurken kullanılacak temel adresini belirtmek için bu metin kutusunu kullanabilirsiniz.  
  
 **Hata ayıklama bilgileri üret**  
 Seçin **hiçbiri**, **tam**, veya **yalnızca pdb** listeden. **Hiçbiri** hata ayıklama bilgisi oluşturulacağını belirtir. **Tam** tam hata ayıklama bilgilerini oluşturulan gerektiğini belirtir ve **yalnızca pdb** yalnızca PDB hata ayıklama bilgilerini oluşturulacağını belirtir. Varsayılan olarak, bu seçeneği ayarlamak **tam**.  
  
## <a name="compilation-constants"></a>Derleme sabitleri  
 Koşullu derleme sabitleri sahip efekt, kullanmanın benzer bir [#Const](http://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) önişlemci yönergesi bir kaynak dosya, tanımlı sabitler herkese açık ve projedeki tüm dosyalar için geçerlidir. Koşullu derleme sabitleri ile birlikte kullanabileceğiniz [#If... Then... #Else](http://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) yönergesi, kaynak dosyaları koşullu olarak derleyebilirsiniz. Bkz: [koşullu derleme](http://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).  
  
 **DEBUG sabitini tanımlayın**  
 Varsayılan olarak, bir hata ayıklama sabit ayarlanması belirterek bu onay kutusu seçilidir.  
  
 **TRACE sabitini tanımlayın**  
 Varsayılan olarak, TRACE sabitini ayarlanması belirterek bu onay kutusu seçilidir.  
  
 **Özel sabitleri**  
 Bu metin kutusunda, uygulamanızın herhangi özel bir sabit girin. Girişleri bu formu kullanarak virgülle ayrılmış: **Name1 "Value1", Name2 = "Value2", Name3 = "Value3"**.  
  
## <a name="other-settings"></a>Diğer ayarlar  
 **Serileştirme bütünleştirilmiş kodları üret**  
 Bu ayar, derleyicinin XML serileştirme derlemeleri oluşturacak olup olmadığını belirtir. Serileştirme derlemeleri başlatma performansını geliştirebilir <xref:System.Xml.Serialization.XmlSerializer> kodunuzda türleri serileştirmek için bu sınıfı kullandıysanız. Varsayılan olarak, bu seçeneği ayarlamak **otomatik**, yalnızca kullandıysanız, serileştirme derlemelerinin oluşturulacağını belirten <xref:System.Xml.Serialization.XmlSerializer> kodunuzdaki XML kodlama. **Kapalı** serileştirme derlemelerinin hiçbir zaman, kodunuzun kullanıp bağımsız olarak oluşturulmamasını belirtir <xref:System.Xml.Serialization.XmlSerializer>. **Üzerinde** serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme derlemeleri yeniden adlandırılır `TypeName`. XmlSerializers.dll.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)



