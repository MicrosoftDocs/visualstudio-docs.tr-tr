---
title: 'Nasıl yapılır: Kod Merkezi birincil kaynağı ile hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 090326e2bc86aee9acc6e9cee92bc518f64ad63d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800191"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Nasıl Yapılır: Kod Merkezi Birincil Kaynağı ile Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İle [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] hata ayıklayıcı, Microsoft MSDN Kod Merkezi birincil güvenli paylaşılan kaynaktan hata ayıklaması yapabilirsiniz.  
  
 Bu konu başlığı altında ayarlamak ve Visual Studio'da kod merkezi birincil kaynak kodunda hata ayıklamak açıklanmaktadır.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Kod Merkezi birincil ile hata ayıklama için hazırlamak için  
  
1. Akıllı kart okuyucu bağlanmak ve paylaşılan kaynak girişimi aldığınız kart ekleyin.  
  
2. Visual Studio'yu başlatın.  
  
3. Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.  
  
4. İçinde **seçenekleri** açık iletişim kutusunu **hata ayıklama** düğüm ve tıklatın **genel**.  
  
5. NET **yalnızca benim kodumu etkinleştir (sadece yönetilen)** onay kutusu.  
  
6. Seçin **kaynak sunucusu desteğini etkinleştir**.  
  
7. NET **özgün sürümle kaynak dosyaların uyuşmasını gerektir**.  
  
8. Altında **hata ayıklama** düğümünü tıklatın **sembolleri**.  
  
9. İçinde **sembol dosyası (.pdb) konumlar** kutusunun işaretini kaldırın **Microsoft Server sembolleri** onay kutusunu işaretleyin ve aşağıdaki konumlardan ekleyin:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  Eğik yazdığınızdan emin olun<strong>/</strong> yolun sonuna.  
  
     Bu konumlar, bu sembolleri ilk yüklenmesini sağlamak için listenin en üstüne taşıyın.  
  
   > [!NOTE]
   >  Yüklenen ilk konumları olmasını sağlamak Bu kod merkezi birincil konumlar listelenmesi gerekir. Visual Studio 2010'da, yukarıdaki herhangi bir sunucuya taşınamaz **Microsoft sembol sunucuları** onay kutusunu temizlemeniz gerekir neden olan giriş.  
   > 
   >  Sembolleri Microsoft hata ayıklama oturumu sırasında sembolleri için şunu yapın:  
   > 
   > 1. Üzerinde **hata ayıklama** menüsünde seçin **Windows** seçip **modülleri**.  
   >    2.  Semboller için istediğiniz modülü seçin ve ardından kısayol menüsünü açın. Seçin **sembolleri şuradan Yükle** seçip **Microsoft sembol sunucuları**.  
  
10. İçinde **sembolleri sembol sunucularından bu dizindeki önbellek** kutusunda, bir konum girin `C:\symbols` burada kod merkezi birincil önbellek simgeleri. Semboller önbelleğe alma, hata ayıklama sırasında performansını önemli ölçüde artırabilir.  
  
     Kaynak kodu ile hata ayıklama sorunlarla karşılaşırsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu yordamı tamamladıktan sonra daha önce önbelleğe alınmış ve eski sembol dosyaları için Önbellek konumunu denetleyin. Güncel olmayan sembol dosyalarını kaldırın.  
  
11. **Tamam**'ı tıklatın.  
  
12. Yeniden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ayarlarını kalıcı olmasını sağlamak için.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>İşleme İliştir kullanarak kaynak kodunuz hata ayıklamak için  
  
1.  Akıllı kart okuyucu bağlanmak ve paylaşılan kaynak girişimi aldığınız kart ekleyin.  
  
2.  Visual Studio'yu başlatın.  
  
3.  Visual Studio projenizi açın.  
  
4.  Üzerinde **Araçları** menüsünü tıklatın **iliştirme**.  
  
5.  İçinde **iliştirme** iletişim kutusu, tıklayın **seçin**.  
  
6.  İçinde **kod türünü seç** iletişim kutusunun **bu tür kodlarda algılamak**seçin **yerel**, **yönetilen**, ve **yönetilen () v4.0)**.  
  
7.  Tıklayın **Tamam** kapatmak için **kod türünü seç** iletişim kutusu.  
  
8.  İçinde **kullanılabilir işlemler** kutusunda, hata ayıklamak istediğiniz işlemi seçin.  
  
9. Tıklayın **ekleme**.  
  
10. Sertifikanızı onaylamanız istendiğinde, tıklayın **Tamam**. Ardından PIN'İNİZİ girin. Kod Merkezi birincil kullanım koşullarını kabul, siz istenirse kullanılır.  
  
     Semboller indiriliyor, çok sayıda ağ hızına bağlı olarak zaman alabilir. Tüm semboller başarıyla indirildi, durum çubuğunu gösterir.  
  
11. Çözümünüzdeki tüm yönetilen projeleri için ek adımları yineleyin.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Varolan bir çözüm kaynak kodundan hata ayıklamak için  
  
1. İçinde **Çözüm Gezgini**, çözüm için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2. Çözüm özellik sayfaları iletişim kutusunda seçin **kaynak dosyalarında Hata Ayıkla** içinde **ortak özellikler** düğümü.  
  
3. Şu konuma ekleme **kaynak dosyaları içeren dizinler** listesi:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  Eğik yazdığınızdan emin olun<strong>/</strong> yolun sonuna.  
  
4. Çözümünüzdeki her yönetilen proje için aşağıdakileri yapın  
  
   1.  Çözüm Gezgini'nde, proje için kısayol menüsünü açın ve ardından **özellikleri**.  
  
   2.  Seçin **hata ayıklama** seçip **unmanged kod hata ayıklamayı**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Çözümünüzü kod merkezi birincil kaynağı ile hata ayıklamak için  
  
1.  İçinde `Package` sınıfı, paket Oluşturucu bir kesme noktası ayarlayın.  
  
2.  İçinde `Debug` menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
3.  Paket oluşturucu içinde kesme noktasına ulaştığınızda, Git **çağrı yığını** penceresini açın ve sonra simgeler, yüklemek istediğiniz derlemenin yığın çerçevesi sağ tıklayın **yük sembolleri**.  
  
     Kaynak yüklemek için çağrı çerçevesi çift tıklayın.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Kod Merkezi birincil kaynak koduna gidin  
  
1.  Akıllı kart okuyucu bağlanmak ve paylaşılan kaynak girişimi aldığınız kart ekleyin.  
  
2.  Internet Explorer başlatma aşağıdaki URL'yi girin: `https://codepremium.msdn.microsoft.com`  
  
3.  İstediğiniz kaynak bulmak için Gözat'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Kod Merkezi birincil](http://www.microsoft.com/resources/sharedsource/ccp.mspx)



