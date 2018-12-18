---
title: "İzlenecek yol: Profiler API'lerini kullanarak | Microsoft Docs"
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
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab545d338defb3876145c8ac648574484fbf89a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749078"
---
# <a name="walkthrough-using-profiler-apis"></a>İzlenecek yol: Profilini Oluşturucu API'ler Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İzlenecek yol, nasıl kullanılacağını göstermek için bir C# uygulaması kullanır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profil Araçları API'leri. Profil Oluşturucu API izleme profil oluşturma sırasında toplanan veri miktarını sınırlamak için kullanın.  
  
 Bu kılavuzda açıklanan adımları, genellikle bir C/C++ uygulamasına uygulanır. Her dil için derleme ortamınıza uygun bir şekilde yapılandırmanız gerekir.  
  
 Genellikle, örnek profil oluşturma kullanarak uygulama performansını analiz etmek başlar. Örnek profil oluşturma bir performans sorunu saptıyor bilgi sağlamazsa, profil oluşturma araçları büyük bir ayrıntı düzeyi sağlar. Profil oluşturma araçları, iş parçacığı etkileşim araştırmak için çok kullanışlıdır.  
  
 Ancak, büyük bir ayrıntı düzeyini daha fazla veri toplandığı anlamına gelir. Profil oluşturma Araçları'nı büyük veri dosyalarını oluşturduğunu görebilirsiniz. Ayrıca, izleme uygulamanın performansını etkileyen daha yüksektir. Daha fazla bilgi için [izleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md) ve [örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)  
  
 Visual Studio Profil Oluşturucu veri koleksiyonu sınırlamanıza olanak sağlar. Bu izlenecek yol, profil oluşturucu API kullanarak veri koleksiyonunu sınırlamak nasıl bir örnek sağlar. Visual Studio profil oluşturucu uygulamaya denetleme veri toplama için bir API sağlar.  
  
 Yerel kod için Visual Studio profil oluşturucu API içinde VSPerf.dll'lardır. Üst bilgi dosyası VSPerf.h ve içeri aktarma kitaplığını VSPerf.lib, Microsoft Visual Studio 9\Team Araçlar\Performans araçları dizininde yer alır.  
  
 Yönetilen kod için profil oluşturucu API içinde Microsoft.VisualStudio.Profiler.dll'lardır. Bu DLL Microsoft Visual Studio 9\Team Araçlar\Performans araçları dizininde bulunur. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzda, hata ayıklama ve örnekleme desteklemek üzere tercih ettiğiniz geliştirme ortamında yapılandırılmış varsayılır. Aşağıdaki konular bu Önkoşullar genel bir bakış sağlar:  
  
 [Nasıl Yapılır: Toplama Metotlarını Seçme](../profiling/how-to-choose-collection-methods.md)  
  
 [Nasıl Yapılır: Başvuru Pencereleri Sembol Bilgileri](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Profil Oluşturucu başlatıldığında, varsayılan olarak, profil oluşturucu genel düzeyde veri toplar. Aşağıdaki kod programın başında, profil oluşturma genel kapatır.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Bir API çağrısı kullanmadan komut satırında veri toplamayı kapatabilirsiniz. Aşağıdaki adımlar, profil oluşturma araçları çalıştırmak için yapılandırılmış komut satırı derleme ortamınızı varsayar ve geliştirme araçlarınızı olarak. Bu Vsınstr ve VSPerfCmd için gereken ayarları içerir. Komut satırı profil oluşturma araçları bakın.  
  
## <a name="limiting-data-collection-using-profiler-apis"></a>Profiler API'lerini kullanarak veri toplama sınırlaması  
  
#### <a name="to-create-the-code-to-profile"></a>Profil için kod oluşturmak için  
  
1.  Visual Studio'da yeni bir C# projesi oluşturun veya bir komut satırı derleme, tercihinize bağlı olarak kullanın.  
  
    > [!NOTE]
    >  Yapı, Microsoft Visual Studio 9\Team Araçlar\Performans araçları dizininde Microsoft.VisualStudio.Profiler.dll kitaplığı başvurmalıdır.  
  
2.  Kopyalama ve projenize aşağıdaki kodu yapıştırın:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Toplamak ve Visual Studio IDE içinde verileri görüntülemek için  
  
1. Açık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Oturum **Çözümle** menüsünde **Profiler**ve ardından **yeni performans oturumu.**  
  
2. Derlenmiş ikili dosyanız için ekleme **hedefleri** listesinde **performans Gezgini** penceresi. Sağ **hedefleri**ve ardından **hedef ikili Ekle**. İkili dosyada bulun **hedef ikili Ekle** iletişim kutusunu ve ardından **açık**.  
  
3. Seçin **izleme** gelen **yöntemi** listesini **performans Gezgini** araç çubuğu.  
  
4. Tıklayın **başlatma profil oluşturma ile**.  
  
    Profil Oluşturucu izleme ve ikili yürütür ve bir performans raporu dosyası oluşturun. Performans Raporu dosyası görünür **raporları** düğümünün **performans Gezgini**.  
  
5. Ortaya çıkan performans raporu dosyası açın.  
  
   Profil Oluşturucu başlatıldığında, varsayılan olarak, profil oluşturucu genel düzeyde veri toplar. Aşağıdaki kod programın başında, profil oluşturma genel kapatır.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Toplamak ve komut satırında verileri görüntülemek için  
  
1.  Hata ayıklama sürümü "Profili kod oluşturma" yordamı, bu kılavuzda daha önce oluşturduğunuz örnek kodu derleyin.  
  
2.  Yönetilen bir uygulama profili oluşturmak için uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:  
  
     **VsPefCLREnv /traceon**  
  
3.  Aşağıdaki komutu yazın:**Vsınstr \<filename > .exe**  
  
4.  Aşağıdaki komutu yazın:**VSPerfCmd çalıştığından/Output:\<filename > .vsp**  
  
5.  Aşağıdaki komutu yazın:**VSPerfCmd /globaloff**  
  
6.  Programınızı çalıştırın.  
  
7.  Aşağıdaki komutu yazın:**VSPerfCmd/Shutdown**  
  
8.  Aşağıdaki komutu yazın:**VSPerfReport/calltrace:\<filename > .vsp**  
  
     Geçerli dizin performans elde edilen verilerle bir .csv dosyası oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Visual Studio Profiler API Başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Çalışmaya başlama](../profiling/getting-started-with-performance-tools.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)



