---
title: Visual Studio Kabuğu (tümleşik) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb0c8dd0588e1af9b3aad500c8bc9f899b44513
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765276"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Kabuğu (tümleşik)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio tümleşik kabuğu, tümleşik geliştirme ortamı (IDE), hata ayıklayıcı ve kaynak denetimi tümleştirmesini içerir. Herhangi bir programlama dili dahil edilir. Ancak, tümleşik kabuk programlama dilleri eklemenize olanak tanıyan bir altyapı sağlar.  
  
 Visual Studio tümleşik kabuğu, Visual Studio yalıtılmış Kabuğu yanı sıra tümleşik Kabuk belirli bileşenler içeren bir ek yükleme aslında bir birleşiminden oluşur.  Tümleşik Kabuk uygulamanızı hem yalıtılmış Kabuk yeniden dağıtılabilir paketi içermelidir [Microsoft Visual Studio Kabuğu (yalıtılmış) yeniden dağıtılabilir paket](http://go.microsoft.com/fwlink/?LinkId=616022) tümleşik Kabuk yeniden dağıtılabilir paketi yanı sıra gelen [Microsoft Visual Studio Kabuğu (tümleşik) yeniden dağıtılabilir paket](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Yalıtılmış ve tümleşik Kabuk yeniden dağıtılabilir paketlerine erişebilmeniz için önce bir kısa bir müşteri anketini doldurmanız istenir.  Anketi doldurduktan sonra yeniden dağıtılabilir paket indirme bağlantılarının ile Visual Studio Connect sayfasına yönlendirilirsiniz.  Visual Studio Connect sitesi altında daha sonra gerçekleştirdiğiniz ziyaretlerde indirme bağlantıları bulabilirsiniz **programlar &#124; VISUAL STUDIO 2015 TÜMLEŞİK ve YALITILMIŞ KABUK** sekmesi.  
  
 Tümleşik Kabuk uygulamanızı Visual Studio'nun tam sürümünü aynı bilgisayara yüklerseniz, uygulamanızın bileşenleri doğrudan Visual Studio'ya tümleştirilecektir.  
  
## <a name="features-in-the-integrated-shell"></a>Tümleşik Kabuk özellikleri  
  
|||  
|-|-|  
|Özellik alanı|Özellik|  
|Dil Desteği|-Yok|  
|IDE|<ul><li>Ayarlar<br /><br /> <ul><li>Ayarları oluşturma</li><li>İçeri ve dışarı aktarma ayarları</li><li>Ayarları sıfırlama</li></ul></li><li>**Araç kutusu** tümleştirme</li><li>**Görev listesi** tümleştirme</li><li>Yardım tümleştirmesi</li><li>**Seçenekleri** iletişim kutusu</li><li>Yazı tipleri ve renkler Yönetimi</li><li>**Çıkış** penceresi</li><li>**Komut** penceresi</li><li>Pencere Yönetimi</li><li>Komutlar, menüler ve tuş bağlamaları</li><li>Etki alanına özgü dil (DSL) çalışma zamanı</li></ul>|  
|Proje sistemi ve proje türleri|-Çözüm ve çözüm klasörleri<br />-Çözüm Yapılandırma Yöneticisi<br />-Öğesi yönetimi<br />-Tek proje ve birden çok proje çözümleri<br />-Uygulama Tasarımcısı'nı (Basitleştirilmiş Proje Özellikleri)<br />-Web Başvurusu Ekle<br />-Hizmet Başvurusu Ekle<br />Tek proje<br />-Web sitesi proje türleri<br />-Web uygulama projeleri|  
|Derleme|-IDE'de özel derleme adımları<br />-Önceden derleme fikri mülkiyet (IP) koruma<br />-Kod imzalama<br />     MSBuild|  
|Düzenleyici|-Koda göz atma (birleştirilmiş arama, kaynak tanımı, devralma) araçları<br />-Kod Gezintisi<br />-IntelliSense<br />-Akıllı etiketler<br />-Yeniden düzenleme<br />-Düzgün listeleme<br />-IntelliSense filtreleme<br />-   **Kod tanımı** penceresi|  
|Tasarımcı|-Windows Presentation Foundation Tasarımcısı<br />-Windows Forms Tasarımcısı<br />-Web Tasarımcısı ve HTML düzenleyicisi|  
|Veri|-   **Sunucu Gezgini** (Basitleştirilmiş: yalnızca verileri). Bkz. Not 1.<br />-   **Veri kaynakları** penceresi<br />-Tam kümesini veri denetimleri<br />-XML Düzenleyicisi<br />-Veri bağlama için yerel veri kaynağı (. MDF veya. MDB)<br />-Veri nesnesine bağlama<br />-Veri Web hizmetine bağlama<br />-Yerel veritabanı sunucusuna veri bağlama<br />-Uzak veritabanı sunucusu veri bağlama<br />-DDL uzak veri için Araçlar<br />-   **Sunucu Gezgini** genişletilebilirlik ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] örnekleri)|  
|Hata Ayıklayıcısı|-Yerel hata ayıklama. Bkz. Not 2.<br />-Yönetilen hata ayıklama<br />-Yerel hata ayıklama<br />-Yerel işleme<br />-Uzaktan işleme<br />-Anonim temsilci<br />-Uygulama etki alanları<br />-ASPX hata ayıklama<br />-Attributes<br />-Func-değerlendirmesi sırasında kesme<br />-Kesme noktaları<br />-Kesme noktası kısıtlamaları<br />-Çağrı yığını<br />-   **Komut** penceresi<br />-İş parçacıkları arası hata ayıklama<br />-Veri ipuçları<br />-Veri Görselleştirici<br />-Yönetilen hata ayıklama Yardımcıları (Mda'lar) hata ayıklayıcı desteği<br />-Tür ileticisi hata ayıklayıcı desteği<br />-Dteeevents OTB desteği<br />-JMC adımlayıcıdaki<br />-Hata ayıklayıcı AppID test (DBGCLR)<br />-Hata ayıklayıcı profili<br />-Hata ayıklayıcı Araçlar ve Seçenekler<br />-Hata ayıklama yineleyici<br />-Tasarım zamanı ifade değerlendirmesi<br />-C# ifade değerlendiricisi<br />-Ayrıştırma<br />-Düzenle ve devam et<br />-İfade değerlendirici windows (izleme, Yereller, Otolar)<br />-Özel durum Yardımcısı<br />-Özel durumları<br />-Yürütme<br />-Genel türler<br />-Doğru kaynağı alma<br />-HPC/küme hata ayıklama<br />-Tümleşik çoklu dil hata ayıklama<br />-Birlikte çalışma hata ayıklama<br />-Just-ın-time hata ayıklama<br />-Yerel hata ayıklama<br />-Yönetilen hata ayıklama<br />-El ile denetim (işlemler penceresi)<br />-Bellek<br />-Mini döküm desteği<br />-Modüller<br />-Çok işlemli hata ayıklama<br />-Yerel hata ayıklama<br />-Yeni hata ayıklama altyapısı desteği<br />-Optimize edilmiş kodda hata ayıklama<br />-Çıkış windows filtreleme<br />-Barındırma yönetilen hata ayıklama için işleme<br />-İşlemler<br />-Quickwatch<br />-Kaydeder<br />-Stack kayıtlara<br />-Uzaktan hata ayıklama<br />-Dönüş değerleri<br />-Komut dosyası hata ayıklama<br />-Kaynak hizmet desteği<br />-Güvenlik<br />-Yan<br />-SQL<br />-Sembol sunucusu<br />-İzleme noktaları<br />-İş parçacığı<br />-Görsel öğeler<br />-Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) hata ayıklayıcı|  
|64-bit desteği|-64-bit hem yönetilen hem de yerel kod için tüm dillerde hata ayıklama<br />-x64 yerel destek|  
|Kaynak kodu denetimi (SCC)|-Temel SCC tümleştirmesi. Bkz. Not 3.<br />-Araçlar ve Seçenekler doğrulama|  
|Genişletilebilirlik|-VSPackages ve MEF Bileşenleri kullanma|  
  
## <a name="notes"></a>Notlar  
  
#### <a name="1-data-tools"></a>1. Veri Araçları  
 Veritabanı geliştirme araçları ve Basitleştirilmiş veri genişletilebilirlik desteği gibi tümleşik Kabuk içerir **Çözüm Gezgini**. Ancak, SQL Server Express, SQL Raporlama ve Crystal Reports tümleşik Kabuğu dahil edilmez.  
  
#### <a name="2-debugging-support"></a>2. Hata ayıklama desteği  
 Tümleşik Kabuk, Visual Studio Community sürümü dahil aynı hata ayıklama altyapısını içerir. Hata ayıklama altyapısı gibi Ekle, kesme noktası ayarlayın, Düzenle ve devam et ve diğer yaygın hata ayıklayıcı için yönetilen kod ve ilgili özellikleri içerir. Ancak, hata ayıklama Altyapısı SQL Server veritabanı hata ayıklamayı desteklemiyor.  
  
 Ancak destek yerel hata ayıklama, temel hata ayıklayıcı paket içerisine dâhil için ek dilleri desteklemek için genişletilemez.  
  
#### <a name="3-source-code-control-integration"></a>3. Kaynak kodu denetimi tümleştirmesinin  
 Tümleşik kabuğu, kaynak kodu denetimi (SCC) uygulamak için ve tümleştirme bileşenlerini MSSCCI tabanlı ortak kaynak denetimi sağlamak için API'ler sağlar.  
  
 SCC tümleştirmesi Pro sürümü Visual Studio'nun normal bir özellik olmamasına karşın, SCC tümleştirmesi tümleşik Kabuğu'nda sağlanır.  
  
#### <a name="4-build-support"></a>4. Derleme desteği  
 Tümleşik Kabuk derleme desteği sağlar. Derlemelerde hakkında bilgi bulabilirsiniz [MSBuild başvurusu](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Tümleşik Kabuğu'nda bulunmayan özellikler  
 Tümleşik Kabuğu'nda bulunmayan özelliklerin bir listesi verilmiştir:  
  
-   Sınıf Tasarımcısı  
  
-   Önleyici DotFuscator  
  
-   Dil özellikleri  
  
-   VSHost  
  
-   Hiçbir Visual Studio dilleri veya ilişkili proje şablonları veya proje öğesi şablonları, tümleşik Kabuğu dahil edilir. Hiçbir dil özgü diğer özellikleri, örneğin Visual Basic kod parçacıkları için dahil edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio genel bakışı genişletme](http://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)