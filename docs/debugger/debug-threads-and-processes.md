---
title: İş parçacıklarında ve işlemlerde hata ayıklama araçları | Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb8c8abab1dc4b8f5778ed4b76688f8a3946e461
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888835"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>İş parçacıklarında ve işlemlerde Visual Studio'da hata ayıklama araçları
*İş parçacığı* ve *işlemleri* bilgisayar biliminde ilişkili kavramlardır. Her ikisi de belirli bir sırayla yürütülmesi gereken yönerge sıralarını temsil eder. Ayrı iş parçacıkları veya işlemlerdeki, yönergeleri, ancak paralel olarak çalıştırabilirsiniz.  
  
 İşlemler, işletim sistemi içinde bulunur ve kullanıcıların programlar ya da uygulamalar gördükleri için karşılık gelir. Bir iş parçacığı, diğer yandan, bir işlem içinde bulunur. Bu nedenle, iş parçacığı olarak da adlandırılır *basit işlemler*. Her işlem, bir veya daha fazla iş parçacığından oluşur.  
  
 Birden çok işlemin varlığı, bir bilgisayar aynı anda birden fazla görev gerçekleştirmesini sağlar. Birden çok iş parçacığı varlığını işi paralel olarak ayırmak bir işlem sağlar. Çok işlemcili bir bilgisayarda, işlemlere veya iş parçacıklarına farklı işlemciler üzerinde çalıştırabilirsiniz. Bu, doğru paralel işlemeye olanak tanır.  
  
 Mükemmel paralel işleme her zaman mümkün değildir. İş parçacıklarının bazen eşitlenmesi gerekir. Bir iş parçacığı için başka bir iş parçacığından bir sonuç beklkemek zorunda kalabilir veya bir iş parçacığı başka bir iş parçacığının kullandığı kaynağa özel erişim gerekebilir. Eşitleme, yaygın bir nedeni, çok iş parçacıklı uygulamalarda hata sorunlardır. Bazen iş parçacıkları, hiçbir zaman kullanılabilir duruma bir kaynağı bekleyen durumda sonlandırabiliriz. Bu adlı bir koşul olur *kilitlenme*.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hata ayıklayıcı iş parçacıklarında ve işlemlerde hata ayıklama için güçlü ancak kullanımı kolay araçlar sağlar.  
  
## <a name="tools-and-features"></a>Araçları ve özellikleri
Kullanmak için ihtiyacınız olan araçları [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne tür kod hata ayıklama çalıştığınız bağlıdır:

- İşlemler için birincil araçlardır **iliştirme** iletişim kutusu, **işlemleri** penceresinde ve **hata ayıklama konumu** araç çubuğu.

- İş parçacığı için iş parçacıklarında hata ayıklama için kullanılan birincil Araçlar olan **iş parçacıkları** penceresinde, kaynak pencerelerdeki iş parçacığı işaretçileri **Paralel Yığınlar** penceresinde **paralel izleme** penceresinde ve **hata ayıklama konumu** araç çubuğu.  
  
- Kullanan kod için <xref:System.Threading.Tasks.Task> içinde [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), [eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime/) (yerel kod için), çok iş parçacıklı uygulamalarda hata ayıklama için kullanılan birincil Araçlar olan**Paralel Yığınlar** penceresinde **paralel izleme** penceresinde ve **görevleri** penceresi ( **görevleri** penceresi de destekler JavaScript promise nesnesi).

- GPU iş parçacıklarında hata ayıklama için birincil araçtır **GPU iş parçacıkları** windows.  
  
  Aşağıdaki tabloda kullanılabilir bilgileri gösterir ve eylemleri, bu yerlerin her birinde gerçekleştirebilirsiniz:  
  
|Kullanıcı Arabirimi|Bilgi yok|Gerçekleştirebileceğiniz eylemler|  
|--------------------|---------------------------|-----------------------------|  
|**İşleme** iletişim kutusu|Ekleyebileceğiniz kullanılabilir işlemler:<br /><br /> -İşlem adı (.exe)<br />-İşlem kimlik numarası<br />-MenüÇubuğu başlığı<br />-Type (yönetilen v4.0; Yönetilen v2.0, v1.1, v1.0; x86; x64; IA64)<br />-Kullanıcı adı (hesap adı)<br />-Oturum sayısı|Eklemek için bir işlem seçin<br /><br /> Bir uzak bilgisayar seçin<br /><br /> Uzak bilgisayarlara bağlanmak için aktarım türünü değiştirme|  
|**İşlemler** penceresi|Eklenen işlemler:<br /><br /> -İşlem adı<br />-İşlem kimlik numarası<br />-.exe işlemek için yol<br />-MenüÇubuğu başlığı<br />-Durum (kesme. Çalıştıran)<br />-Hata ayıklama (yönetilen, yerel vb.)<br />-Aktarım Türü (varsayılan, kimlik doğrulama olmadan yerel)<br />-Aktarım niteleyicisi (uzak bilgisayar)|Araçlar:<br /><br /> -Ekleme<br />-Ayırma<br />-Sonlandır<br /><br /> Kısayol menüsü:<br /><br /> -Ekleme<br />-Ayırma<br />-Hata ayıklama durdurulduğunda ayırma<br />-Sonlandır|  
|**İş parçacığı** penceresi|Geçerli işlemdeki iş parçacıkları:<br /><br /> -İş parçacığı kimliği<br />-Yönetilen kimliği<br />-Kategori (ana iş parçacığı, arabirimi iş parçacığı, uzak yordam çağrı işleyicisi veya çalışan iş parçacığı)<br />-İş parçacığı adı<br />-İş parçacığının oluşturulduğu konum<br />-Öncelik<br />-Benzeşim maskesi<br />-Askıda sayma<br />-İşlem adı<br />-Bayrak göstergesi<br />-Askıda gösterge|Araçlar:<br /><br /> -Arama<br />-Arama isteği yığını<br />-Sadece benim kodumu işaretle<br />-Bayrak Özel Modül Seçimi<br />-Gruplandırma ölçütü<br />-Sütunları<br />-Genişlet/Daralt çağrı yığınını<br />-Grupları Genişlet/Daralt<br />-Dondurma/çözme iş parçacığı<br /><br /> Kısayol menüsü:<br /><br /> -Kaynakta iş parçacıklarını Göster<br />-Bir iş parçacığına geçiş<br />-Bir çalışan iş parçacığını Dondur<br />-Dondurulmuş bir iş parçacığını devam ettir<br />-Ek çalışma için bir iş parçacığı bayrak<br />-Bir iş parçacığının işaretini kaldır<br />-Bir iş parçacığını yeniden adlandır<br />-Göster ve iş parçacıklarını Gizle<br /><br /> Diğer eylemler:<br /><br /> -Bir DataTip içinde bir iş parçacığı için çağrı yığınını görüntüleme|  
|Kaynak penceresi|Sol kanaldaki iş parçacığı göstergeleri, tek veya birden çok iş parçacığı belirtin (varsayılan olarak, kısayol menüsünü kullanarak açık, kapalı **iş parçacıkları** pencere)|Kısayol menüsü:<br /><br /> -Bir iş parçacığına geçiş<br />-Ek çalışma için bir iş parçacığı bayrak<br />-Bir iş parçacığının işaretini kaldır|  
|**Hata ayıklama konumu** araç çubuğu|-Geçerli işlem<br />-Uygulamayı Askıya Al<br />-Uygulamayı sürdürmek<br />-Askıya alma ve uygulamayı kapatın<br />-Geçerli iş parçacığı<br />-Geçerli iş parçacığı bayrak durumunu değiştir<br />-Yalnızca bayraklı iş parçacıklarını Göster<br />-Yalnızca geçerli işlemi göster<br />-Geçerli yığın çerçevesi|-Başka bir işleme geçiş yap<br />-Askıya alma, sürdürme veya uygulamayı kapatın<br />-Geçerli işlemdeki başka bir iş parçacığına geçiş<br />-Geçerli iş parçacığındaki başka bir yığın çerçevesine geçiş<br />-Geçerli iş parçacıklarını işaretleme veya<br />-Yalnızca bayraklı iş parçacıklarını Göster<br />-Yalnızca geçerli işlemi göster|  
|**Paralel Yığınlar** penceresi|-Tek bir pencerede birden çok iş parçacığı için yığınları çağırın.<br />-Her iş parçacığı için etkin yığın çerçevesi.<br />-İçin çağıranlar ve çağrılanlar herhangi bir yöntem.|-Belirtilen iş parçacıklarını filtreleme<br />-Görevler görünümüne geçin<br />-Bir iş parçacığını işaretleme veya<br />-Yakınlaştırma|   
|**Paralel izleme** penceresi|-Özel dikkat edilmesi gereken istediğiniz bir iş parçacığını işaretle Bayrak sütunu.<br />-Bir ok Seçilen çerçevenin gösterir çerçeve sütunu.<br />-Makine, işlem, döşeme, görev ve iş parçacığı görüntüleyebilen yapılandırılabilir bir sütun.|-Bir iş parçacığını işaretleme veya<br />-Yalnızca bayraklı iş parçacıklarını görüntüleme<br />-Çerçeveleri Değiştir<br />-Bir sütunu sırala<br />-Grup iş parçacıkları<br />-Dondurma veya çözme iş parçacığı<br />-Paralel İzleme penceresinde verileri dışarı aktarma| 
|**Görevleri** penceresi|-Hakkında bilgileri görüntüleyin <xref:System.Threading.Tasks.Task> nesneleri, görev kimliği, görev durumu (zamanlanmış, çalışıyor, beklemede, kilitli) ve göreve hangi iş parçacığının atanır.<br />-Çağrı yığını geçerli konumu.<br />-Oluşturma zamanında göreve iletilen temsilci|-Geçerli göreve geçiş yap<br />-Bir görevi işaretleme veya<br />-Dondurma veya çözme görevi|  
|**GPU iş parçacıkları** penceresi|-Özel dikkat edilmesi gereken istediğiniz bir iş parçacığını işaretle Bayrak sütunu.<br />-Sarı bir ok geçerli iş parçacığı gösterir geçerli iş parçacığı sütunu.<br />- **İş parçacığı sayısı** sütunuyla aynı konumda iş parçacığı sayısını görüntüler.<br />- **Satırı** her iş parçacığı grubunun bulunduğu kod satırını görüntülüyor sütunu.<br />- **Adresi** her iş parçacığı grubunun bulunduğu yönerge adresini görüntüleyen bir sütun.<br />- **Konumu** kodun konumu adresi olan sütun.<br />- **Durumu** iş parçacığının etkin veya engellenmiş olup olmadığını gösteren bir sütun.<br />- **Döşeme** satırdaki iş parçacıkları için döşeme dizinini gösteren sütunu.|-Farklı bir iş parçacığına değiştirme<br />-Belirli döşeme ve iş parçacığı görüntüle<br />-Bir sütunu sakla ya da görüntüle<br />-Bir sütuna göre sırala<br />-Grup iş parçacıkları<br />-Dondurma veya çözme iş parçacığı<br />-Bir iş parçacığını işaretleme veya<br />-Yalnızca bayraklı iş parçacıklarını görüntüleme|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalıştırma işlemleri iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [GPU Kodunda Hata Ayıklama](../debugger/debugging-gpu-code.md)