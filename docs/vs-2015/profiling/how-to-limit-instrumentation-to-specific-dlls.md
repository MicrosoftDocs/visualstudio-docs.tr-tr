---
title: "Nasıl yapılır: belirli DLL'ler için izleme sınırlama | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 054a281d445f5910e9a2d635bb453dd283425453
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803467"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Nasıl yapılır: Belirli DLL'ler için İzleme Sınırlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İzleme profil oluşturma metodunu kullanarak bir uygulama bir veya daha fazla dll için profil oluşturma verilerinin toplanmasını sınırlayabilirsiniz. Bir uygulama bir veya daha fazla dll profilini çıkarmak için hedefler olarak .dll dosyalarını içeren bir performans oturumu oluşturun. Projelerinde olarak profilini oluşturmak istediğiniz DLL'leri belirleyebilirsiniz bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü ya da bağımsız ikili dosyaları olarak.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Visual Studio çözümünde belirli DLL'ler için izleme sınırlama  
  
1.  DLL'de içeren çözümü açın [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Üzerinde **Çözümle** menüsünde **performans Sihirbazını Başlat**.  
  
3.  Seçin **izleme** 'a tıklayın ve profil oluşturma yöntemi olarak **sonraki**.  
  
4.  Gelen **aşağıdaki kullanılabilir hedeflerden hangisi için profil ister misiniz?**, .dll proje adını seçin ve ardından **sonraki**.  
  
5.  Tıklayın **son** sihirbazdan çıkın ve yeni performans oturumu görüntülemek için **performans Gezgini** penceresi.  
  
6.  Sağ **hedefleri** seçip **hedef Proje Ekle**.  
  
7.  Gelen **hedef Proje Ekle** listesinde, DLL kullanmak için kullanmak istediğiniz yürütülebilir projeyi seçin.  
  
     İsteğe bağlı. İstediğiniz herhangi bir DLL projelerinde profiline ekleyebilirsiniz.  
  
8.  Eklenen bir proje için veri toplama önlemek için proje adına sağ tıklayın ve ardından temizleyin **gereç** onay kutusu.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Profil için belirli DLL'ler bağımsız ikili dosyaları belirtmek için  
  
1.  Açık [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Üzerinde **Çözümle** menüsünde **performans Sihirbazını Başlat**.  
  
3.  Gelen **aşağıdaki kullanılabilir hedeflerden hangisi için profil istediğiniz**seçin **bir dinamik bağlantı kitaplığı profili (. DLL)** ve ardından **sonraki**.  
  
4.  Sihirbazın ikinci sayfasında, aşağıdaki adımları gerçekleştirin:  
  
    -   Profilinde istediğiniz .dll dosyası yolu ve dosya adını yazın **Dll yolu**. Dosyayı bulmak için üç nokta düğmesini (…) de tıklatabilirsiniz **dinamik bağlantı kitaplığı profili** iletişim kutusu. Ardından seçtiğiniz yürütülebilir (.exe) dosyası tarafından başlatılan .dll dosyasının kopyasını belirtmeniz gerektiğini unutmayın.  
  
    -   .dll alıştırma yürütülebilir (.exe) dosya yolu ve dosya adını yazın **yürütülebilir dosya yolu**. Dosyayı bulmak için üç nokta düğmesini (…) de tıklatabilirsiniz **başlatılacak yürütülebilir** iletişim kutusu.  
  
    -   İsteğe bağlı. Yürütülebilir dosyaya geçirilecek istediğiniz komut satırı bağımsız değişkenleri girin **komut satırı bağımsız değişkenleri**. Gerekirse, uygulama için çalışma dizini belirtin **çalışma dizini**.  
  
    -   **İleri**'ye tıklayın.  
  
5.  Seçin **izleme** 'a tıklayın ve profil oluşturma yöntemi olarak **sonraki**.  
  
6.  Tıklayın **son** sihirbazdan çıkın ve yeni performans oturumu görüntülemek için **performans Gezgini** penceresi.  
  
7.  İsteğe bağlı. Daha fazla .dll dosyaları eklemek için sağ **hedefleri** seçip **hedef ikili Ekle**. Dosyaları Seç **hedef ikili Ekle** iletişim kutusu.  
  
    > [!NOTE]
    >  DLL'leri sınayan yürütülebilir (.exe) dosyayı belirtmeyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri toplama denetimi](../profiling/controlling-data-collection.md)   
 [Nasıl Yapılır: İzlemeyi Belirli Araçlarla Sınırlama](../profiling/how-to-limit-instrumentation-to-specific-functions.md)



