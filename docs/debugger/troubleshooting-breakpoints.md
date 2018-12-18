---
title: Hata ayıklayıcı kesme noktaları sorunlarını giderme | Microsoft Docs
ms.custom: seodec18
ms.date: 01/23/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e27d9dee1713b8d9e748ad13d75d809f2057f24a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052857"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında kesme noktaları sorunlarını giderme

## <a name="breakpoint-warnings"></a>Kesme noktası uyarıları

Hata ayıklarken bir kesme noktası iki olası görsel durumlar vardır: kırmızı bir daire ve (beyaz doldurulmuş) bir boş daire. Hata ayıklayıcı başarıyla hedef işlemde bir kesme noktası ayarlamak için kırmızı bir daire kalır. Kesme noktası bir daireye ise, kesme noktasını devre dışı bırakıldı veya kesme noktası ayarlanmaya çalışılırken uyarı oluştu. Farkı belirlemek için kesme noktası gelin ve bir uyarı olup olmadığına bakın.

Aşağıdaki iki bölümü tanınmış uyarıları ve nasıl düzeltileceğini açıklar. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Sembol, bu belge için yüklenmiş" 

Git **modülleri** penceresi (**hata ayıklama** > **Windows** > **modülleri**) ve modülünüzde olup olmadığını denetleyin yüklendi.  
* Modülünüzün yüklenirse, kontrol **sembol durumu** sembolleri yüklenmiş olup olmadığını görmek için sütun. 
  * Semboller yüklenmedi, sorunu tanılamak için Sembol durumunu denetleyin. Bir modülde bağlam menüsünden **modülleri** penceresinde tıklayın **sembol yükleme bilgisi...**  nerede deneyin ve simgeleri yüklemek için hata ayıklayıcı baktığı görmek için. Sembolleri yükleme hakkında daha fazla bilgi için bkz. [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Sembol yüklenmedi, PDB, kaynak dosyaları hakkındaki bilgileri içermiyor. Birkaç olası nedenleri şunlardır: 
    * Kaynak dosyalarını yakın zamanda eklenmişse, güncel sürümü modülün yüklendiği onaylayın.  
    * Kesilmiş Pdb'lerin kullanarak oluşturmak mümkündür **/pdbstrıpped** bağlayıcı seçeneği. Kesilmiş Pdb'lerin kaynak dosya bilgileri içermez. Tam PDB ve kesilmiş bir PDB çalışıyor onaylayın.  
    * PDB dosyası kısmen bozuk. Dosyayı silin ve sorunu çözmeye modülün bir temiz yapı gerçekleştirin. 

* Modülünüzün yüklü değilse, nedenini bulmak için şunları denetleyin: 
  * Doğru işlem hata ayıklaması yaptığınız onaylayın. 
  * Doğru türde bir kod hata ayıklaması yaptığınız denetleyin. Hata ayıklayıcının hata ayıklamak üzere yapılandırılmış kod türünü bulabilirsiniz **işlemleri** penceresi (**hata ayıklama** > **Windows**  >  **İşlemleri**). C# kodu hatalarını ayıklama çalışıyorsanız, örneğin, .NET Framework'ün uygun bir tür için hata ayıklayıcı yapılandırıldığından emin olun (örneğin, yönetilen (v4\*) yönetilen karşılaştırması (v2\*/v3\*) yönetilen (CoreCLR) yerine). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… Geçerli kaynak kodunu yerleşik... sürümünden farklı." 

Bir kaynak dosyası değiştirilirse ve kaynak artık ayıkladığınız kod ile eşlenmiyorsa, hata ayıklayıcı kesme noktaları kodda varsayılan olarak ayarlamaz. Normalde, bu sorun, bir kaynak dosyası değiştirildi, ancak kaynak kodunu yeniden değildi gerçekleşir. Bu sorunu gidermek için projeyi yeniden derleyin. Aksi halde proje zaten güncel olduğundan derleme sistemi gördüğü, kaynak dosyasını yeniden kaydederek ya da yeniden oluşturmanız veya projenin temizleyerek derleme çıkışı derlemeden önce proje sisteminin zorlayabilirsiniz. 

Nadir senaryolarda, eşleşen kaynak koduna gerekmeden hata ayıklamak isteyebilirsiniz. Kaynak kodu ile eşleşen hata ayıklama kafa karıştırıcı bir adayı hata ayıklama deneyimi, bu nedenle olduğundan bu nasıl devam etmek istediğinizden emin yapabilirsiniz.  

Bu güvenlik denetimleri devre dışı bırakmak için aşağıdakilerden birini yapın: 
* Tek bir kesme noktası değiştirmek için düzenleyicide kesme noktası simgesinin üzerine gelin ve ayarları (dişli) simgesini tıklatın. Bir Özet penceresi Düzenleyicisi'ne eklenir. Göz atma penceresinin en üstünde bir kesme noktası konumunu belirten bir köprü yoktur. Kesme noktası konumu değiştirilmesine izin verir ve denetlemek için köprüyü tıklatarak **kaynak kodun özgün sürümden farklı olmasına izin ver**.
* Tüm kesme noktalarını için bu ayarı değiştirmek için Git **hata ayıklama** > **seçenekler ve ayarlar**. Üzerinde **hata ayıklama/genel** sayfasında, NET **özgün sürümle tam eşleşen kaynak dosyaları gerekiyor** seçeneği. İşiniz bittiğinde bu seçenek yeniden etkinleştirmek emin hata ayıklama. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Kesme noktası (uyarı yok) başarıyla ayarlandı, ancak isabet gelmedi 

Bu bölümde, tüm uyarıların hata ayıklayıcı görüntülenmiyor – etkin bir şekilde hata ayıklarken kesme noktası kırmızı bir daire olduğundan henüz kesme noktasına isabet değil karşılaşılan sorunları gidermek için bilgi sağlar. 

Denetlenecek bazı işlemler aşağıda verilmiştir: 
1. Kodunuzu birden fazla işlem veya birden fazla bilgisayarda çalışıyorsa, doğru işlem ya da bilgisayar ayıkladığınız emin olun.  
2. Kodunuzun çalıştığını onaylayın. Kodunuzun çalıştığı test etmek için bir çağrı ekleyin `System.Diagnostics.Debugger.Break` (C# /VB) veya `__debugbreak` (C++) nerede kesme noktası ayarlayın ve ardından projenizi yeniden derleyin aktarmaya çalıştığınız kod satırına. 
3. En iyi duruma getirilmiş kod hata ayıklaması yapıyorsanız emin olun, Kesme noktasının ayarlandığı işlevi olan olmayan başka bir işleve satır içine alınmış. `Debugger.Break` Önceki iade etme açıklanan test, test bu sorunu de çalışabilir. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Bir kesme noktası sildim ama hata ayıklamayı yeniden başlattığınızda, isabet devam 

Hata ayıklarken bir kesme noktası sildiyseniz, hata ayıklama yeniden başlattığınızda kesme noktasına isabet. Bu kesme noktasına ulaşma durdurmak için kesme noktası örneklerini kaldırılma tüm emin **kesme noktaları** penceresi.  
