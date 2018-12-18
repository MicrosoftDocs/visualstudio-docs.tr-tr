---
title: Hata Listesi penceresi | Microsoft Docs
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
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0ecec77428d32512ec1b5fcf3822933c1c619b7f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873713"
---
# <a name="error-list-window"></a>Hata Listesi Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[NOT]
>  Hata listesi, belirli bir hata iletisi hakkındaki bilgileri görüntüler. Hata numarasını veya hata dizesi metnini çıktı penceresinden kopyalayabilirsiniz. Çıktı penceresini görüntülemek için Ctrl + Alt + O tuşlarına basın. Bkz: [çıkış penceresi](../../ide/reference/output-window.md).  
  
 Kullanarak uygulamalarınızı daha hızlı geliştirebilirsiniz **hata listesi** penceresi. Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
- Hatalar, uyarılar ve kod yazdığınız sırada üretilen iletileri görüntüleyin.  
  
- IntelliSense tarafından fark edilen sözdizimi hatalarını bulur.  
  
- Bulma dağıtım hatalarını, belirli statik analiz hatalarını ve kurumsal şablon ilkeleri uygulanırken saptanan hataları.  
  
- Burada sorun ortaya çıkar ve hata konumuna gitmek dosyayı açmak için hata iletisini çift tıklayın.  
  
- Hangi girişlerin görüntüleneceğini ve her giriş için hangi bilgi sütunlarını görünür filtreleyin.  
  
- Özel terimleri arayın ve yalnızca geçerli proje veya belgeyi aramayı kapsamına.  
  
  Görüntülenecek **hata listesi**, tıklayın **görünüm / hata listesinde**, veya **CTRL +\\+ E**.  
  
  Seçebileceğiniz **hataları**, **uyarıları**, ve **iletileri** farklı düzeylerde bilgileri görmek için sekmeler.  
  
  Listeyi sıralamak için herhangi bir sütun başlığına tıklayın. Başka bir sütuna göre yeniden sıralamak için SHIFT tuşunu basılı tutun ve başka bir sütun başlığına tıklayın. Hangi sütunların görüntülenip hangilerinin gizlendiğini seçmek için seçin **sütunları göster** kısayol menüsünden. Sütunların görüntülenme sırasını değiştirmek için herhangi bir sütun başlığını sola veya sağa sürükleyin.  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz, etkin ayarlarınıza ve sürüm bağlı olarak burada açıklananlar farklılık gösterebilir. Ayarlarınızı değiştirmek için tıklayın **Araçlar / içe ve dışa aktarma ayarları**. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="error-list-filters"></a>Hata listesi filtreleri  
 Araç çubuğunun sağ tarafında biri diğeri araç çubuğunun solunda iki açılır liste kutusu filtrede iki tür vardır. Araç çubuğunun sol tarafta açılır listeden kullanılacak kod dosyalarını belirtir (**çözümün tamamında**, **açık belgeler**, **geçerli proje**,  **Geçerli belge**).  
  
 Analiz etmek ve hata grupları üzerinde hareket için arama kapsamını sınırlandırabilirsiniz. Örneğin, bir projenin derlenmesini önleyen çekirdek hatalarına odaklanmak isteyebilirsiniz. Kapsam belirleme seçenekleri şunlardır:  
  
1. **Belgeleri açma**: hatalar, uyarılar ve açık belgelerin iletileri göster.  
  
2. **Geçerli proje**: Göster hataları, uyarıları ve iletileri seçilmiş belgenin projesinden **Düzenleyicisi** veya seçilen projede **Çözüm Gezgini**.  
  
   > [!NOTE]
   >  Şu anda seçili olan belgenin projesi seçili projeden farklıysa, filtrelenmiş liste hataları, uyarıları ve iletileri değiştirecek **Çözüm Gezgini**.  
  
3. **Geçerli belge**: hatalar, uyarılar ve şu anda seçili belgedeki iletilerini göster **Düzenleyicisi** veya **Çözüm Gezgini**.  
  
   Bir filtre o anda arama sonucuna uygulanırsa, filtrenin adını görünür **hata listesi** başlık çubuğu. **Hataları**, **uyarıları**, ve **iletileri** düğmeleri sonra toplam öğe sayısının yanı sıra gösterilen filtrelenmiş öğe sayısını da görüntüler; örneğin, düğme Göster x / y hata. Hiçbir filtre uygulanmamışsa başlık çubuğunda yalnızca "hata listesi" yazar.  
  
   Araç çubuğunun sağ tarafındaki listenin (bir yapı işleminden kaynaklanan hatalar) derleme hatalarından gösterilip gösterilmeyeceğini belirtir veya IntelliSense (bir derleme çalıştırmadan önce algılanan hataları) veya her ikisi de.  
  
## <a name="search"></a>Ara  
 Kullanım **arama hatası listesi** metin kutusunun sağ alt tarafında **hata listesi** hata Listesi'nde belirli hataları bulmak için araç çubuğu. Hata listesindeki görünen herhangi bir sütunda arama yapabilirsiniz ve arama sonuçları her zaman sorgu veya uygulanan filtre yerine sıralama önceliği olan sütun göre sıralanır. Seçerseniz **Esc** odak modundayken anahtar **hata listesi**, arama terimini temizleyebilir ve arama sonuçlarını filtrelersiniz. Ayrıca **X** temizleyin metin kutusunun sağ tarafındaki.  
  
## <a name="save"></a>Kaydet  
 Hata listesini kopyalayabilir ve bir dosyaya kaydedin. Kopyala ve seçimi sağ tıklayın ve ardından bağlam menüsünde istediğiniz hataları seçin **kopyalama**. Ardından, hataları bir dosyaya yapıştırabilirsiniz. Hataları bir Excel elektronik tablosuna yapıştırırsanız, alanlar farklı sütunlar olarak görünür.  
  
## <a name="ui-element-list"></a>UI öğe listesi  
 Önem Derecesi  
 Farklı türde görüntüler **hata listesi** giriş (**hata**, **ileti**, **uyarı**, **uyarı (etkin)**, **(Devre dışı) uyarı**.  
  
 Kod  
 Hata kodu görüntülenir.  
  
 Açıklama  
 Giriş metni görüntüler.  
  
 Proje  
 Geçerli projenin adını görüntüler.  
  
 Dosya  
 Dosya adını görüntüler.  
  
 Çizgi  
 Sorun oluştuğu satırı görüntüler.



