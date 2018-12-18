---
title: GPU kodunda hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c0fdab78364eaf4c0f9fd86753b8ca1c4178415
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677726"
---
# <a name="debugging-gpu-code"></a>GPU Kodunda Hata Ayıklama
Grafik işlemci birimi (GPU) üzerinde çalışan C++ kodu hata ayıklaması yapabilirsiniz. GPU hata ayıklama desteği Visual Studio'da yarış algılama işlemlerini başlatma ve bunları ve hata ayıklama Windows tümleştirme ekleme içerir.  
  
## <a name="supported-platforms"></a>Desteklenen Platformlar  
 Hata ayıklama desteklenir [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)], ve [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)]. Yazılım benzetmesi üzerinde hata ayıklama [!INCLUDE[win8](../debugger/includes/win8_md.md)], veya [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] gereklidir. Donanım üzerinde hata ayıklamak için ekran kartınızın sürücülerini yüklemeniz gerekir. Tüm donanım satıcıları, tüm hata ayıklayıcı özellikler uygular. Sınırlamalar satıcı belgelerine bakın.  
  
> [!NOTE]
>  Visual Studio GPU hata ayıklama desteklemek istediğiniz bağımsız donanım satıcıları kendi sürücüleri hedefleri ve VSD3DDebug arabirimi uygulayan bir DLL oluşturmanız gerekir.  
  
## <a name="configuring-gpu-debugging"></a>GPU hata ayıklama yapılandırma  
 Hata ayıklayıcı, hem CPU kod hem de GPU kodu aynı uygulama yürütme kesemez. Varsayılan olarak, hata ayıklayıcı CPU kodu keser. GPU kodunda hata ayıklamak için aşağıdaki iki adımlardan birini kullanın:  
  
-   İçinde **hata ayıklama türü** listesini **standart** araç seçin **yalnızca GPU**.  
  
-   İçinde **Çözüm Gezgini**, projenin kısayol menüsünde **özellikleri**. İçinde **özellik sayfaları** iletişim kutusunda **hata ayıklama**ve ardından **yalnızca GPU** içinde **hata ayıklayıcı türü** listesi.  
  
## <a name="launching-and-attaching-to-applications"></a>Başlatma ve uygulamalarına iliştirme  
 Visual Studio hata ayıklama komutları başlatmak ve GPU hata ayıklamayı durdurmak için kullanabilirsiniz. Daha fazla bilgi için [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md). Bu işlemin GPU kodu yürütür, GPU hata ayıklayıcısı ancak çalışan bir işleme ekleyebilirsiniz. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>İmleç ve imlece kadar Çalıştır geçerli parçayı Çalıştır  
 GPU üzerinde hata ayıklama için İmleç konumuna çalıştırmak için iki seçeneğiniz vardır. Her iki seçenek için komutlar, kod düzenleyicinin kısayol menüsünden kullanılabilir.  
  
1.  **İmlece kadar Çalıştır** İmleç konumuna ulaşıncaya ve sonra kesildiğinde kadar uygulamanız komutu çalıştırır. Bu, geçerli iş parçacığının imlece çalıştırıldığında göstermez; Bunun yerine, imleç noktasına ulaştığında ilk iş parçacığında sonu tetikler anlamına gelir. Bkz: [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)  
  
2.  **İmlece kadar geçerli Kutucuğuna çalıştırma** komutu tüm iş parçacıklarının geçerli kutucuğunda imleç ve ardından sonları ulaşana kadar uygulamanızı çalıştırır.  
  
## <a name="debugging-windows"></a>Windows hata ayıklama  
 Belirli hata ayıklama pencerelerini kullanarak, inceleyin, bayrak ve GPU iş parçacıklarını Dondur. Daha fazla bilgi için bkz.:  
  
-   [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)  
  
-   [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)  
  
-   [Nasıl Yapılır: Paralel İzleme Penceresini Kullanma](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [İş parçacıklarında ve işlemlerde hata ayıklama](../debugger/debug-threads-and-processes.md) (hata ayıklama konumu araç çubuğu)  
  
-   [Nasıl Yapılır: GPU İş Parçacıkları Penceresini Kullanma](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>Veri eşitleme özel durumları  
 Hata ayıklayıcı yürütme sırasında birkaç veri eşitleme koşullar tanımlayabilirsiniz. Bir koşul algılandığında, hata ayıklayıcı kesme durumuna girer. İki seçeneğiniz vardır —**sonu** veya **devam**. Kullanarak **özel durumları** iletişim kutusu, hata ayıklayıcı Bu koşullar algılar ve ayrıca hangi koşullar Bu için keser olup olmadığını yapılandırabilirsiniz. Daha fazla bilgi için [yönetme özel durumları hata ayıklayıcısı ile](../debugger/managing-exceptions-with-the-debugger.md). Ayrıca **seçenekleri** yazılan veriler veri değerini değiştirmez, hata ayıklayıcısını özel durumlar yoksayması gerektiğini belirtmek için iletişim kutusu. Daha fazla bilgi için [genel, hata ayıklama, Seçenekler iletişim kutusu](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="troubleshooting"></a>Sorun giderme  
  
### <a name="specifying-an-accelerator"></a>Bir Hızlandırıcı belirtme  
 Kod çalışıyorsa, GPU kodda kesme noktaları isabet yalnızca [accelerator::direct3d_ref](/cpp/parallel/amp/reference/accelerator-class#direct3d_ref) (REF) Hızlandırıcı. Kodunuzda bir Hızlandırıcı belirtmezseniz, REF Hızlandırıcı olarak otomatik olarak seçilir **hata ayıklama Hızlandırıcı türü** proje özelliklerinde. Kodunuzu açıkça bir Hızlandırıcı seçerse, REF Hızlandırıcı, hata ayıklama sırasında kullanılmaz ve hata ayıklama desteği, GPU donanım sahip olmadığı sürece kesme noktaları isabet edilmeyecektir. Hata ayıklama sırasında REF Hızlandırıcısını kullanır, böylece kod yazarak bunu çözebilirsiniz. Daha fazla bilgi için bkz: Proje özelliklerini ve [Hızlandırıcı ve accelerator_view nesnelerini kullanma](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) ve [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="conditional-breakpoints"></a>Koşullu kesme noktaları  
 GPU kodunda koşullu kesme noktaları desteklenir ancak her ifade cihazda değerlendirilebilir. Cihazda bir ifade değerlendirilemiyor, hata ayıklayıcıyı değerlendirilir. Hata ayıklayıcı, cihaz daha yavaş çalışmasına olasıdır.  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Hata: Seçili hata ayıklama Hızlandırıcı türü ile bir yapılandırma sorunu var.  
 Proje ayarlarını ve yapılandırmasını üzerinde hata ayıklama bilgisayar arasında bir tutarsızlık olduğunda bu hata oluşur. Daha fazla bilgi için [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Hata: Seçili hata ayıklama Hızlandırıcı türü için hata ayıklama sürücüsü hedef makinede yüklü değil.  
 Uzak bir bilgisayarda hata ayıklaması yapıyorsanız, bu hata oluşur. Hata ayıklayıcı, çalışma zamanına kadar sürücüleri uzak Bilgisayarına yüklü olup olmadığını belirleyemiyor. Grafik kartı üreticisinden sürücüleri kullanılabilir.  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Hata: Zaman aşımı algılama ve Kurtarma (TDR) uzak sitede devre dışı bırakılmalıdır.  
 Windows zaman aşımı algılama ve kurtarma işlemi (TDR) tarafından ayarlanmış varsayılan zaman aralığını aşan C++ AMP hesaplamalar için mümkündür. Bu durum oluştuğunda, hesaplama iptal edilir ve veriler kaybolur. Daha fazla bilgi için [işleme TDRs C++ amp'de](http://go.microsoft.com/fwlink/p/?LinkId=249154).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: C++ AMP uygulamasında hata ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Visual Studio GPU hata ayıklamayı Başlat](http://go.microsoft.com/fwlink/p/?LinkId=255381)