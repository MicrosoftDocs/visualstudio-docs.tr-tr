---
title: "İzlenecek yol: Profiler API'lerini kullanarak | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e5baebb527c09d833e405a98bd701ad02b7fe86
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928067"
---
# <a name="walkthrough-using-profiler-apis"></a>İzlenecek yol: Profil oluşturucu API'ler Kullanma

İzlenecek yol, nasıl kullanılacağını göstermek için bir C# uygulaması kullanır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Araçları API'leri. Profil Oluşturucu API izleme profil oluşturma sırasında toplanan veri miktarını sınırlamak için kullanın.  
  
 Bu kılavuzda açıklanan adımları, genellikle bir C/C++ uygulamasına uygulanır. Her dil için derleme ortamınıza uygun bir şekilde yapılandırmanız gerekir.  
  
 Genellikle, örnek profil oluşturma kullanarak uygulama performansını analiz etmek başlar. Örnek profil oluşturma bir performans sorunu saptıyor bilgi sağlamazsa, profil oluşturma araçları büyük bir ayrıntı düzeyi sağlar. Profil oluşturma araçları, iş parçacığı etkileşim araştırmak için çok kullanışlıdır.  
  
 Ancak, büyük bir ayrıntı düzeyini daha fazla veri toplandığı anlamına gelir. Profil oluşturma Araçları'nı büyük veri dosyalarını oluşturduğunu görebilirsiniz. Ayrıca, izleme uygulamanın performansını etkileyen daha yüksektir. Daha fazla bilgi için [izleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md) ve [örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)  
  
 Visual Studio Profil Oluşturucu veri koleksiyonu sınırlamanıza olanak sağlar. Bu izlenecek yol, profil oluşturucu API kullanarak veri koleksiyonunu sınırlamak nasıl bir örnek sağlar. Visual Studio profil oluşturucu uygulamaya denetleme veri toplama için bir API sağlar.  
  
 Yerel kod için Visual Studio profil oluşturma API'leri bulunan *VSPerf.dll*. Üstbilgi dosyası *VSPerf.h*ve içeri aktarma kitaplığını *VSPerf.lib*, bulunan *Microsoft Visual Studio 9\Team Araçlar\Performans Araçları* dizin.  
  
 Yönetilen kod için profil oluşturucu API bulunan *Microsoft.VisualStudio.Profiler.dll*. Bu DLL bulunan *Microsoft Visual Studio 9\Team Araçlar\Performans Araçları* dizin. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzda, hata ayıklama ve örnekleme desteklemek üzere tercih ettiğiniz geliştirme ortamında yapılandırılmış varsayılır. Aşağıdaki konular bu Önkoşullar genel bir bakış sağlar:  
  
 [Nasıl yapılır: Toplama metotlarını seçme](../profiling/how-to-choose-collection-methods.md)  
  
 [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Profil Oluşturucu başlatıldığında, varsayılan olarak, profil oluşturucu genel düzeyde veri toplar. Aşağıdaki kod programın başında, profil oluşturma genel kapatır.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Bir API çağrısı kullanmadan komut satırında veri toplamayı kapatabilirsiniz. Aşağıdaki adımlar, profil oluşturma araçları çalıştırmak için yapılandırılmış komut satırı derleme ortamınızı varsayar ve geliştirme araçlarınızı olarak. Bu Vsınstr ve VSPerfCmd için gereken ayarları içerir. Bkz: [komut satırı profil oluşturma araçları](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## <a name="limit-data-collection-using-profiler-apis"></a>Profil Oluşturucu API'ler kullanma sınırı veri toplama  
  
#### <a name="to-create-the-code-to-profile"></a>Profil için kod oluşturmak için  
  
1.  Visual Studio'da yeni bir C# projesi oluşturun veya bir komut satırı derleme, tercihinize bağlı olarak kullanın.  
  
    > [!NOTE]
    >  Derleme başvurmalıdır *Microsoft.VisualStudio.Profiler.dll* bulunan kitaplık, *Microsoft Visual Studio 9\Team Araçlar\Performans Araçları* dizin.  
  
2.  Kopyalama ve projenize aşağıdaki kodu yapıştırın:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication1  
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

                    A a = new A(2);  
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis()); 

                    DataCollection.StartProfile(  
                    ProfileLevel.Global,  
                    DataCollection.CurrentId);

                    int x;  
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
  
1. Açık [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Oturum **Çözümle** menüsünde **Profiler**ve ardından **yeni performans oturumu**.  
  
2. Derlenmiş ikili dosyanız için ekleme **hedefleri** listesinde **performans Gezgini** penceresi. Sağ **hedefleri**ve ardından **hedef ikili Ekle**. İkili dosyada bulun **hedef ikili Ekle** iletişim kutusunu ve ardından **açık**.  
  
3. Seçin **izleme** gelen **yöntemi** listesini **performans Gezgini** araç çubuğu.  
  
4. Tıklayın **başlatma profil oluşturma ile**.  
  
    Profil Oluşturucu izleme ve ikili yürütür ve bir performans raporu dosyası oluşturun. Performans Raporu dosyası görünür **raporları** düğümünün **performans Gezgini**.  
  
5. Ortaya çıkan performans raporu dosyası açın.  
  
   Profil Oluşturucu başlatıldığında, varsayılan olarak, profil oluşturucu genel düzeyde veri toplar. Aşağıdaki kod programın başında, profil oluşturma genel kapatır.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Toplamak ve komut satırında verileri görüntülemek için  
  
1.  Hata ayıklama sürümü "Profili kod oluşturma" yordamı, bu kılavuzda daha önce oluşturduğunuz örnek kodu derleyin.  
  
2.  Yönetilen bir uygulama profili oluşturmak için uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:  
  
     **VsPerfCLREnv /traceon**  
  
3.  Aşağıdaki komutu yazın: **Vsınstr \<filename > .exe**  
  
4.  Aşağıdaki komutu yazın: **VSPerfCmd çalıştığından/Output:\<filename > .vsp**  
  
5.  Aşağıdaki komutu yazın: **VSPerfCmd /globaloff**  
  
6.  Programınızı çalıştırın.  
  
7.  Aşağıdaki komutu yazın: **VSPerfCmd/Shutdown**  
  
8.  Aşağıdaki komutu yazın: **VSPerfReport/calltrace:\<filename > .vsp**  
  
     A. *csv* ortaya çıkan performans verileri geçerli dizin dosyası oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Visual Studio profil oluşturucu API Başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Çalışmaya başlama](../profiling/getting-started-with-performance-tools.md)   
 [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
