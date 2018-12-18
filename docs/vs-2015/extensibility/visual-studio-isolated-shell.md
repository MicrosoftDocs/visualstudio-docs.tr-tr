---
title: Visual Studio yalıtılmış Kabuğu | Microsoft Docs
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
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7fcb0a838f2849ab74d202785709164ec5af6d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740663"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio yalıtılmış Kabuğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio yalıtılmış Kabuğu yan yana çalıştırabileceğiniz tek başına uygulamalar oluşturmanıza olanak tanır, Visual Studio'nun diğer sürümleriyle birlikte. Bu, öncelikle Visual Studio Hizmetleri kullanın ancak özelleştirilmiş bir görünüm de özel araçlar barındırmak için kullanılan ve marka olur. Visual Studio özellikleri ve menü komut gruplarını, kolayca açılıp kapatılabilir. Uygulama başlıkları, uygulama simgeleri ve Karşılama ekranları tamamen özelleştirilebilir. Özelleştirilebilir özelliklerinin listesi için bkz. [yalıtılmış Kabuğu özelleştirme](../extensibility/customizing-the-isolated-shell.md).  
  
 Bir yalıtılmış Kabuk proje ile çalışmak için Visual Studio SDK'yı yüklemeniz gerekir. Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Yalıtılmış Kabuk uygulaması oluşturmak için Visual Studio Kabuğu yalıtılmış bir projeyle başlayın. Bu proje kendi yalıtılmış Kabuk uygulaması geliştirin ve çalıştırın gereken her şeyi içerir. Dağıtır, uygulamanızın Kurulum programını yazmak hazır olduğunuzda, yalıtılmış Kabuk yeniden dağıtılabilir paketi almalısınız [Microsoft Visual Studio Kabuğu (yalıtılmış) yeniden dağıtılabilir paket](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Yalıtılmış Kabuk yeniden dağıtılabilir paketi erişebilmeniz için önce bir kısa bir müşteri anketini doldurmanız istenir.  Anketi doldurduktan sonra yeniden dağıtılabilir paket indirme bağlantılarının ile Visual Studio Connect sayfasına yönlendirilirsiniz.  Visual Studio Connect sitesi altında daha sonra gerçekleştirdiğiniz ziyaretlerde indirme bağlantıları bulabilirsiniz **programlar &#124; VISUAL STUDIO 2015 TÜMLEŞİK ve YALITILMIŞ KABUK** sekmesi.  
  
> [!NOTE]
>  Yalıtılmış kabuk tabanlı bir uygulama dağıtma hakkında daha fazla bilgi için bkz. [izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Yalıtılmış Kabuk ile çalışma  
 Visual Studio yalıtılmış Kabuk uygulaması, Visual Studio services tam erişimi olduğundan ve özel özelleştirme ve markalama destekler. Yalıtılmış Kabuk uygulaması özelleştirebilirsiniz birkaç yolu vardır:  
  
- VSPackages ve Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçalarına yalnızca bunları başka bir Visual Studio Uzantısında kullandığınız gibi yalıtılmış Kabuk uygulaması genişletmek için kullanabilirsiniz. Daha fazla bilgi için [yalıtılmış Kabuğu genişletme](../extensibility/extending-the-isolated-shell.md).  
  
- Visual Studio özellikleri ve menü komut gruplarını kullanılabilir veya kullanılamaz hale getirmek için uygulamanın kullanıcı arabirimini (UI) projede .vsct dosyası güncelleştirin.  
  
- Kaldırılacak **seçenekleri** sayfaları veya Visual Studio shell bileşenlerini uygulamadan güncelleştirme uygulamanın .pkgundef dosyası.  
  
- Diğer yönleri görünümü veya kabuk davranışını değiştirmek için uygulamanın .pkgdef dosyası güncelleştirin.  
  
- Uygulama başlatıldığında Kabuk bazı yönlerini de belirtilebilir. Bunu yapmak için yapılan çağrıda appenvstub.dll başlangıç giriş noktası parametreleri güncelleştirin.  
  
  Özelleştirebileceğiniz farklı öğeler hakkında daha fazla bilgi için bkz. [yalıtılmış kabuğun öğeleri](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Yalıtılmış Kabuk standart özellikler  
 Aşağıdaki özellikleri, Visual Studio'nun tüm sürümleri için standarttır.  
  
|Özellik kategorisi|Özellik|  
|----------------------|-------------|  
|IDE özellikleri|Ayarları içeri/dışarı aktarma<br /><br /> Araç kutusu denetimi yükleyici<br /><br /> Görev listesi & hata listesi<br /><br /> Çıktı Penceresi<br /><br /> Başlangıç Sayfası<br /><br /> Özellikler Penceresi<br /><br /> Araç Kutusu<br /><br /> Çözüm Gezgini<br /><br /> Yer işareti penceresi<br /><br /> Sınıf Görünümü<br /><br /> Nesne Tarayıcısı<br /><br /> Komut Penceresi<br /><br /> Belge Anahattı<br /><br /> Kaynak Görünümü<br /><br /> Dış Aracı<br /><br /> Windows Communication Foundation (WCF) hizmet Başvurusu Ekle<br /><br /> Dil tümleşik sorgu (LINQ) desteği|  
|Düzenleyici/Tasarımcısı|Koda göz atma (birleştirilmiş arama, kaynak tanımı, devralma) araçları<br /><br /> IntelliSense<br /><br /> Akıllı etiketler<br /><br /> Kod parçacıkları Yöneticisi<br /><br /> Kod Parçacıkları<br /><br /> Yeniden Düzenle<br /><br /> Düzgün listeleme<br /><br /> IntelliSense filtreleme<br /><br /> Kod tanımı penceresi<br /><br /> Uygulama Tasarımcısı<br /><br /> Windows Form Tasarımcısı<br /><br /> Windows Presentation Foundation (WPF) Tasarımcısı|  
|Hata Ayıklama|C# ifade değerlendiricisi<br /><br /> Yerel hata ayıklama<br /><br /> Yönetilen hata ayıklama<br /><br /> Düzenle ve Devam Et<br /><br /> Çoklu iş parçacığı hata ayıklama<br /><br /> görselleştirmeler<br /><br /> DataTips<br /><br /> Yerel hata ayıklama<br /><br /> Betik hata ayıklama<br /><br /> Birlikte çalışma hata ayıklama<br /><br /> Just-in-time (JIT) hata ayıklama<br /><br /> Çok işlemli hata ayıklama<br /><br /> XSLT hata ayıklama<br /><br /> Yerel işleme<br /><br /> İzleme noktaları<br /><br /> Kesme noktası kısıtlamaları|  
|Veri|Sunucu Gezgini (Basitleştirilmiş - yalnızca verileri)<br /><br /> Veri bağlama için yerel veri (. MDF veya. MDB)<br /><br /> Nesne veri bağlama<br /><br /> Web hizmeti için veri bağlama<br /><br /> Eksiksiz bir veri denetimleri listesi<br /><br /> XML Düzenleyicisi<br /><br /> Verilerin bağlanacağı yerel veritabanı sunucusu<br /><br /> Veri Kaynakları penceresi|  
|Web|HTML Düzenleyicisi<br /><br /> Web tarayıcısı<br /><br /> Web formları Tasarımcısı<br /><br /> Web sitesi projesi<br /><br /> Web uygulama projesi|  
|Genişletilebilirlik|VSPackages ve MEF Bileşenleri kullanır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kabuk (Yalıtılmış veya Tümleşik)](../extensibility/shell-isolated-or-integrated.md)

