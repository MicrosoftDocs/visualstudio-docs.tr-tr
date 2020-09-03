---
title: Hata ayıklama Iş parçacıkları ve süreçler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df9bc7cdb185edd27d7572c1436db442514d38e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202557"
---
# <a name="debug-threads-and-processes"></a>İş Parçacıklarında ve İşlemlerde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İş parçacıkları * ve *süreçler* , bilgisayar bilimi 'ndeki ilgili kavramlardır. Her ikisi de belirli bir sırada yürütülmesi gereken yönergelerin dizilerini temsil eder. Ancak, ayrı iş parçacıkları veya süreçlerdeki yönergeler paralel olarak çalıştırılabilir.  
  
 İşletim sisteminde süreçler bulunur ve kullanıcıların program veya uygulama olarak gördükleri kullanıcılara karşılık gelir. Bir işlem içinde, diğer yandan bir iş parçacığı bulunur. Bu nedenle, iş parçacıkları bazen *hafif süreçler*olarak adlandırılır. Her işlem bir veya daha fazla iş parçacığından oluşur.  
  
 Birden çok işlemin varlığı, bir bilgisayarın bir seferde birden fazla görev gerçekleştirmesini sağlar. Birden çok iş parçacığının varlığı, bir işlemin bir işi paralel olarak gerçekleştirilmesine olanak sağlar. Çok işlemcili bir bilgisayarda, süreçler veya iş parçacıkları farklı işlemcilerde çalışabilir. Bu, doğru paralel işlemeyi mümkün bir şekilde sunar.  
  
 Kusursuz paralel işleme her zaman mümkün değildir. İş parçacıkları bazen eşitlenmelidir. Bir iş parçacığının bir sonucu başka bir iş parçacığından beklemek zorunda kalabilir veya bir iş parçacığının başka bir iş parçacığının kullandığı bir kaynağa özel erişime ihtiyacı olabilir. Eşitleme sorunları, çok iş parçacıklı uygulamalardaki hataların yaygın bir nedendir. Bazen iş parçacıkları hiçbir zaman kullanılamayan bir kaynağı bekliyor olabilir. Bu, *kilitlenme*adlı bir koşula neden olur.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Hata ayıklayıcı, iş parçacıkları ve süreçlerinde hata ayıklamak için güçlü ancak kullanımı kolay araçlar sağlar.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Visual Studio 'da Iş parçacıkları ve süreçler için hata ayıklama araçları  
 ' De işlemlerle çalışmaya yönelik birincil araçlar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **işleme Ekle** Iletişim kutusu, **Işlemler** penceresi ve **hata ayıklama konumu** araç çubuğudur. Hata ayıklama iş parçacıklarının birincil araçları, **Iş parçacıkları** penceresidir, kaynak Windows 'daki iş parçacığı Işaretçileri ve **hata ayıklama konumu** araç çubuğudur.  
  
 Çoklu iş parçacıklı uygulamalarda hata ayıklamaya yönelik başlıca araçlar, paralel **yığınlardır** ve **paralel görevlerdir**, paralel **izleme**ve **GPU iş parçacıkları** Windows.  
  
 Aşağıdaki tabloda, kullanılabilir bilgiler ve bu yerlerden her birinde gerçekleştirebileceğiniz eylemler gösterilmektedir:  
  
|Kullanıcı Arabirimi|Kullanılabilir bilgiler|Gerçekleştirebileceğiniz eylemler|  
|--------------------|---------------------------|-----------------------------|  
|**Işleme İliştir** iletişim kutusu|Ekleyebileceğiniz kullanılabilir süreçler:<br /><br /> -İşlem adı (. exe)<br />-İşlem KIMLIĞI numarası<br />-MenuBar başlığı<br />-Type (yönetilen v 4.0; Yönetilen v 2.0, v 1.1, v 1.0; Itanium x64 IA64<br />-Kullanıcı adı (hesap adı)<br />-Oturum numarası|İliştirilecek bir işlem seçin<br /><br /> Uzak bilgisayar seçin<br /><br /> Uzak bilgisayarlara bağlanmak için taşıma türünü değiştir|  
|**İşlem** penceresi|Ekli süreçler:<br /><br /> -İşlem adı<br />-İşlem KIMLIĞI numarası<br />-Process. exe dosyasının yolu<br />-MenuBar başlığı<br />-State (kesme. Çalıştıran<br />-Hata ayıklama (yerel, yönetilen vb.)<br />-Aktarım türü (varsayılan, kimlik doğrulama olmadan yerel)<br />-Transport niteleyicisi (uzak bilgisayar)|Aracı<br /><br /> -İliştirme<br />-Ayır<br />-Sonlandır<br /><br /> Kısayol menüsü:<br /><br /> -İliştirme<br />-Ayır<br />-Hata ayıklama durdurulduğunda ayır<br />-Sonlandır|  
|**Iş parçacıkları** penceresi|Geçerli işlemdeki iş parçacıkları:<br /><br /> -İş parçacığı KIMLIĞI<br />-Yönetilen KIMLIK<br />-Category (ana iş parçacığı, arabirim iş parçacığı, uzak yordam çağrısı işleyicisi veya çalışan iş parçacığı)<br />-İş parçacığı adı<br />-İş parçacığının oluşturulduğu konum<br />-Öncelik<br />-Benzeşim maskesi<br />-Askıya alınma sayısı<br />-İşlem adı<br />-Bayrak göstergesi<br />-Askıya alınmış gösterge|Aracı<br /><br /> -Ara<br />-Arama yığınında ara<br />-Bayrak Yalnızca kendi kodum<br />-Bayrak özel modül seçimi<br />-Gruplandırma ölçütü<br />-Sütunlar<br />-Callyığınları Genişlet/Daralt<br />-Grupları Genişlet/Daralt<br />-Iş parçacıklarını dondurma/çözme<br /><br /> Kısayol menüsü:<br /><br /> -Kaynakta iş parçacıklarını göster<br />-Bir iş parçacığına geçiş yap<br />-Çalışan bir iş parçacığını dondurma<br />-Dondurulmuş bir iş parçacığını çözme<br />-Ek çalışma için bir iş parçacığına bayrak ekleyin<br />-Bir iş parçacığının bayrağını kaldır<br />-Bir iş parçacığını yeniden adlandırma<br />-İş parçacıklarını gösterme ve gizleme<br /><br /> Diğer eylemler:<br /><br /> -Veri Ipucunda bir iş parçacığının çağrı yığınını görüntüleme|  
|Kaynak penceresi|Sol cilt payındaki iş parçacığı göstergeleri, tek veya birden çok iş parçacığını belirtir (varsayılan olarak, **Iş parçacıkları** penceresinde kısayol menüsü kullanılarak açıktır)|Kısayol menüsü:<br /><br /> -Bir iş parçacığına geçiş yap<br />-Ek çalışma için bir iş parçacığına bayrak ekleyin<br />-Bir iş parçacığının bayrağını kaldır|  
|**Hata ayıklama konumu** araç çubuğu|-Geçerli işlem<br />-Uygulamayı askıya alma<br />-Uygulamayı sürdürür<br />-Uygulamayı askıya alma ve kapatma<br />-Geçerli iş parçacığı<br />-Geçerli iş parçacığı bayrak durumunu değiştirme<br />-Yalnızca bayraklı iş parçacıklarını göster<br />-Yalnızca geçerli işlemi göster<br />-Geçerli yığın çerçevesi|-Başka bir işleme geçiş yap<br />-Uygulamayı askıya alma, sürdürme veya kapatma<br />-Geçerli işlemde başka bir iş parçacığına geçiş yap<br />-Geçerli iş parçacığında başka bir yığın çerçevesine geçiş yap<br />-Geçerli iş parçacıklarını işaretle veya bayrak kaldır<br />-Yalnızca bayraklı iş parçacıklarını göster<br />-Yalnızca geçerli işlemi göster|  
|**Paralel Yığınlar** penceresi|-Birden çok iş parçacığı için yığınları tek bir pencerede çağırın.<br />-Her iş parçacığı için etkin yığın çerçevesi.<br />-Her bir yöntem için çağıranlar ve Callet 'ler.|-Belirtilen iş parçacıklarını filtrele<br />-Paralel Görevler görünümüne geç<br />-Bir iş parçacığını işaretle veya bayrak kaldır<br />-Yakınlaştır|  
|**Paralel görevler** penceresi|- <xref:System.Threading.Tasks.Task> Görev kimliği, görev durumu (zamanlanmış, çalışan, bekleme, kilitli) ve göreve atanan iş parçacığını içeren nesneler hakkında bilgileri görüntüleyin.<br />-Çağrı yığınında geçerli konum.<br />-Temsilci oluşturma zamanında göreve geçildi|-Geçerli göreve geçiş yap<br />-Bir görevi işaretle veya bayrak kaldır<br />-Bir görevi dondurma veya çözme|  
|**Paralel izleme** penceresi|-Özel dikkat etmek istediğiniz bir iş parçacığını işaretlemek için kullanabileceğiniz bayrak sütunu.<br />-Bir okun seçili çerçeveyi gösterdiği çerçeve sütunu.<br />-Makine, işlem, kutucuk, görev ve iş parçacığını görüntüleyebilen yapılandırılabilir bir sütun.|-Bir iş parçacığını işaretle veya bayrak kaldır<br />-Yalnızca bayraklı iş parçacıklarını göster<br />-Kare değiştirme<br />-Bir sütunu sıralama<br />-Grup iş parçacıkları<br />-İş parçacıklarını dondurma veya çözme<br />-Paralel izleme penceresi verileri dışarı aktarma|  
|**GPU Iş parçacıkları** penceresi|-Özel dikkat etmek istediğiniz bir iş parçacığını işaretlemek için kullanabileceğiniz bayrak sütunu.<br />-Sarı okun etkin bir iş parçacığını gösterdiği etkin iş parçacığı sütunu. Bir ok, yürütmenin hata ayıklayıcıya bölünmesinin gerçekleştiği bir iş parçacığını gösterir.<br />-Aynı konumdaki iş parçacığı sayısını görüntüleyen **Iş parçacığı sayısı** sütunu.<br />-Her iş parçacığı grubunun bulunduğu kod satırını görüntüleyen **satır** sütunu.<br />-Her iş parçacığı grubunun bulunduğu yönerge adresini görüntüleyen **Adres** sütunu.<br />-Adresin kodundaki konum olan **Location** sütunu.<br />-İş parçacığının etkin veya engellenmiş olduğunu gösteren **durum** sütunu.<br />-Satırdaki iş parçacıkları için döşeme dizinini gösteren **döşeme** sütunu.|-Farklı bir etkin iş parçacığına geçiş yapın<br />-Belirli bir kutucuğu ve iş parçacığını görüntüleme<br />-Bir sütunu görüntüleme veya gizleme<br />-Sütuna göre sırala<br />-Grup iş parçacıkları<br />-İş parçacıklarını dondurma veya çözme<br />-Bir iş parçacığını işaretle veya bayrak kaldır<br />-Yalnızca bayraklı iş parçacıklarını göster|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [GPU Kodunda Hata Ayıklama](../debugger/debugging-gpu-code.md)
