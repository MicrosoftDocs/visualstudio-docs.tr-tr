---
title: Eşzamanlılık görselleştiricisi komut satırı yardımcı programı (CVCollectionCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a24bea13687d58d4d9b9d9dc8ecf0bec86595759
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951251"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Eşzamanlılık görselleştiricisi komut satırı yardımcı programı (CVCollectionCmd)
Eşzamanlılık görselleştiricisi komut satırı yardımcı programını kullanabilirsiniz (*CVCollectionCmd.exe*) bunları Visual Studio eşzamanlılık görselleştiricisi içinde görüntüleyebilmek komut satırından izlemeleri toplamak için. Araçlar, Visual Studio yüklü olmayan bilgisayarlarda kullanılabilir.  

> [!NOTE]
>  Visual Studio 2013 itibariyle, Concurrency Visualizer isteğe bağlı uzantısıdır. (Daha önce Visual Studio'ya dahil.) İndirebileceğiniz [Eşzamanlılık Görselleştirici toplama araçları Visual Studio 2015 için](http://www.microsoft.com/download/details.aspx?id=49103) İndirme Merkezi'nden.  

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Eşzamanlılık görselleştiricisi komut satırı yardımcı programını indirin  
 Komut satırı yardımcı programını yüklemek ve indirmek için Git [Eşzamanlılık Görselleştirici toplama araçları Visual Studio 2015 için](http://www.microsoft.com/download/details.aspx?id=49103) ve yönergeleri izleyin. Varsayılan olarak, *CVCollectionCmd.exe* %ProgramFiles%\Microsoft eşzamanlılık görselleştiricisi koleksiyon Tools\ içinde yüklenir (% ProgramFiles (x86) %\Microsoft eşzamanlılık görselleştiricisi koleksiyon Tools\ içinde x64 bilgisayarlar).  

## <a name="collect-a-trace-with-cvcollectioncmd"></a>CVCollectionCmd ile bir izleme toplamak  
 Uygulama ile CVCollectionCmd başlatarak veya eklemeyi, bir izleme toplayabilirsiniz. Aşağıdaki komut başvurusu seçenekleri için bkz. Örneğin  

```cmd  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  

## <a name="commands-and-parameters"></a>Komutlar ve parametreler  
 Komut satırı yardımcı programı komutlar ve parametreler hakkında daha fazla yardım almak için bu komut istemine yazın:  

 **CvCollectionCmd /?**  

|Seçenek|Açıklama|Parametreler|Döndürülen değerler|  
|------------|-----------------|----------------|-------------------|  
|Sorgu|Koleksiyon başlatıldı olup olmadığını döndürür.|Yok.|Koleksiyon başlatmaya hazır olup olmadığını 0.<br /><br /> 1 koleksiyonu zaten sürüyor.<br /><br /> Toplama ilerleme durumunu, ancak bir veya daha fazla gerekli içinde değilse 2 [ETW](/dotnet/framework/wcf/samples/etw-tracing) oturumları zaten etkin.|  
|Başlat|Belirtilen işlem eşzamanlılık görselleştiricisi altında çalışır.|Yürütülebilir dosyanın yolu.|çalıştırma başarılı olursa 0.<br /><br /> Hedef uygulama başlatılamadı çünkü çalıştırma başarısız olmuşsa 1.<br /><br /> CVCollectionCmd belirtilen çıkış dizinine yazmak için yeterli izinlere sahip olduğundan çalıştırma başarısız olmuşsa 13.|  
|İliştir|Sistem genelinde izleme toplama başlar; belirtilmişse, aksi takdirde, bir işleme iliştirir.|Yok.|Ek başarılı olursa 0.<br /><br /> 1 ek belirtilen işlemi geçersiz veya belirsiz olduğundan başarısız oldu.<br /><br /> CVCollectionCmd belirtilen çıkış dizinine yazmak için yeterli izinlere sahip olduğundan başarısız oldu, 13.|  
|Ayır|Koleksiyonu durdurur.|Yok.|ayrılmayı başarılı olursa 0.<br /><br /> 1 ayrılmayı koleksiyonu şu anda devam eden olmadığından başarısız oldu.<br /><br /> 2 toplama durdurulamadı ayrılmayı başarısız oldu.|  
|Çözümle|Belirtilen izleme analiz eder.|CVTrace dosyasının tam yolu.|Analiz başarılı olursa 0.<br /><br /> 1 analiz başlatılamadı çünkü belirtilen izleme sistem genelinde, ancak hiçbir hedef işlem belirtildi.<br /><br /> Çözümleme izleme sistem genelinde ve bir işlem olmadığından başlatamıyorsanız, 2 belirtildi.<br /><br /> Belirtilen işlem geçersiz olduğundan çözümleme başarısız olduysa 3.<br /><br /> 4 belirtilen CVTrace dosyasını geçersiz olduğundan çözümleme başarısız oldu.|  
|LaunchArgs|Hedef yürütülebilir bağımsız değişkenleri belirtir. Bu seçenek yalnızca başlatma komutu için geçerlidir.|Uygulama için komut satırı bağımsız değişkenleri.|Yok.|  
|OutDir|İzleme dosyalarının kaydedileceği dizini belirtir. Başlatma ve ek komutlar için geçerlidir.|Bir dizin yolunu veya göreli yol.|Yok.|  
|İşlem|Analiz komutu yürütüldüğünde analiz etmek için bir izleme Ekle komutu ne zaman yürütülen için eklemek için bir işlem veya işlemi belirtir. Attach ve analiz komutları için geçerlidir.|PID veya işlemin adı.|Yok.|  
|Config|Koleksiyon ayarları varsayılan dışındaki istiyorsanız yapılandırma dosyasının yolunu belirtir.   Başlatma, Ekle ve analiz komutları için geçerlidir.|Dizin yolu veya XML yapılandırma dosyasının göreli yolu.|Yok.|  

## <a name="customize-configuration-settings"></a>Yapılandırma ayarlarını özelleştirme  
 Ardından CVCollectionCmd izlemeleri toplamak için kullanın ve koleksiyon ayarlarını özelleştirmek istiyorsanız, bunları belirtmek için bir yapılandırma dosyası kullanın.  

> [!NOTE]
>  İzlemeleri toplamak için Visual Studio kullandığınızda, yapılandırma dosyasını doğrudan değiştirmeyin.  Bunun yerine, [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ayarlarını değiştirmek için iletişim kutusu.  

 Koleksiyon ayarlarını değiştirmek için bir yapılandırma dosyası CVCollectionCmd yardımcı programı çalıştıracağınız makinede oluşturun. Yapılandırma dosyası sıfırdan oluşturabilir veya Visual Studio'nun yüklü olduğu bilgisayarda yapılandırma dosyasını kopyalayıp, değiştirebilirsiniz. Dosyanın nasıl adlandırıldığı *UserConfig.xml* ve bulunan *Yerel AppData* klasör. Yardımcı programını çalıştırdığınızda, yapılandırma seçeneği başlatma, Attach veya Analiz komutu ile birlikte kullanın.  Yapılandırma seçeneği ile ilişkili parametresinde yapılandırma dosyasının yolunu belirtin.  

### <a name="configuration-file-tags"></a>Yapılandırma dosya etiketleri  
 XML-tabanlı yapılandırma dosyasıdır. Geçerli etiketleri ve değerleri şunlardır:  


| Etiket | Açıklama | Değerler |
|-------------------------| - | - |
| Config | Genel yapılandırma dosyası demarcates. | Bu öğeleri içermelidir:<br /><br /> -MinorVersion<br />-MajorVersion |
| MajorVersion | Ana yapılandırma dosyası sürümünü belirtir. | İçin 1 olmalıdır [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projeleri. Aksi durumda 1, yardımcı program çalışmaz. |
| MinorVersion | Yapılandırma dosyası alt sürümünü belirtir. | İçin 0 olmalıdır [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projeleri. Aksi durumda 0, yardımcı program çalışmaz. |
| IncludeEnvSymbolPath | Ortam sembol yolunu (_NT_SYMBOL_PATH) kullanılıp kullanılmayacağını belirleyen değeri ayarlar. | -True<br />-Yanlış |
| DeleteEtlsAfterAnalysis | Analiz tamamlandığında ETL dosyaları silinmiş olup olmadığını belirleyen bir değer ayarlar. | -True<br />-Yanlış |
| SymbolPath | Sembol sunucusu yolunu belirtir. Daha fazla bilgi için [hata ayıklama sembol dosyalarını edinmek için Microsoft sembol Sunucusu'nu kullanma](http://go.microsoft.com/fwlink/?LinkID=149389). | Bir dizin adı veya URL'si. |
| İşaretçileri | İşaretleyicisi sağlayıcılarını listesini içerir. | Sıfır veya daha fazla MarkerProvider öğeler içerebilir. |
| MarkerProvider | Tek işaretleyici sağlayıcısını belirtir. | Bu öğeleri içermelidir:<br /><br /> -Düzeyi<br />-GUID<br />-Ad<br /><br /> Bu öğeleri içerebilir:<br /><br /> -Kategorileri<br />-IsEnabled |
| Düzey | Bir MarkerProvider önem düzeyini ayarlar. | -Düşük<br />-Normal<br />-Yüksek<br />-Kritik<br />-Her şey |
| Guid | ETW işaretleyici sağlayıcısını genel benzersiz tanımlayıcısı. | BİR GUID. |
| Ad | İşaretleyici sağlayıcı açıklamasını belirtir. | Bir dize. |
| Kategoriler | İşaretleyici sağlayıcı için toplanan kategorileri belirtir. | Virgülle ayrılmış bir dize sayı veya sayı aralığı. |
| IsEnabled | İşaretleyici sağlayıcısını koleksiyon için etkin olup olmadığını belirleyen bir değer ayarlar. | -True<br />-Yanlış |
| FilterConfig | Koleksiyondan filtrelenir ETW olayları yapılandırma seçeneklerinin listesini belirtir. | Bu öğeleri içerebilir:<br /><br /> -CollectClrEvents<br />-ClrCollectionOptions<br />-CollectSampleEvents<br />-CollectGpuEvents<br />-CollectFileIO |
| CollectClrEvents | CLR olayları toplanır olup olmadığını belirleyen bir değer ayarlayın. | -True<br />-Yanlış |
| ClrCollectionOptions | Yerel uygulamalar için CLR olayları toplamak etkinleştirilip etkinleştirilmeyeceğini ve NGEN azaltma olaylarını toplamak etkinleştirilip etkinleştirilmeyeceğini belirtir. | Biri, her ikisi de veya hiçbiri bu değerleri içerebilir:<br /><br /> -CollectForNative<br />-DisableNGenRundown |
| CollectSampleEvents | Örnek olaylar toplanan olup olmadığını belirleyen bir değer ayarlar. | -True<br />-Yanlış |
| CollectGpuEvents | DX tarafından oluşturulan olaylar toplanan olup olmadığını belirleyen bir değer ayarlar. | -True<br />-Yanlış |
| CollectFileIO | Dosya g/ç olayları toplanır olup olmadığını belirleyen bir değer ayarlar. | -True<br />-Yanlış |
| UserBufferSettings | Kullanıcı arabelleği ayarlarını parametrelerin listesini belirtir. | Bu öğeleri içermelidir:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers |
| KernelBufferSettings | Çekirdek arabelleği ayarlarını parametrelerin listesini belirtir. | Bu öğeleri içermelidir:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers |
| BufferFlushTimer | Temizleme Zamanlayıcısı ETW arabellek belirtir. | Pozitif bir tamsayı. |
| BufferSize | İçin kilobayt cinsinden, her olay izleme oturumu arabellek atanan bellek miktarı. | 1024 numarası 0. |
| MinimumBuffers | Olay izleme oturumu arabellek havuzu için ayrılan arabellekler en küçük sayısı. | Pozitif bir tamsayı en az iki kez mantıksal çekirdek sayısı. |
| MaximumBuffers | Olay izleme oturumu arabellek havuzu için ayrılan arabellekler maksimum sayısı. | Büyüktür veya eşittir MinimumBuffers sayı. |
| JustMyCode | Yalnızca kendi kodum dizinler listesini belirtir. | Sıfır veya daha fazla MyCodeDirectory öğelerinin listesi. |
| MyCodeDirectory | Kodunuzu içeren dizini belirtir. | Mutlak bir yol. |

### <a name="example"></a>Örnek  
 Bir yapılandırma dosyası en baştan oluşturmak yerine, aşağıdaki örneği kopyalayın ve sonra gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz.  

```xml  
<?xml version="1.0"?>  
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">  

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>  

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>  

  <TraceLocation>C:\traces</TraceLocation>  

  <SymbolPath>http://symweb</SymbolPath>  

  <Markers>  
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />  
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />  
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />  
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />  
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />  
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />  
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />  

    <!-- The IsEnabled and Categories elements are optional -->  
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />  
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />  
  </Markers>  

  <FilterConfig>  
    <CollectClrEvents>true</CollectClrEvents>  
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>  
    <CollectSampleEvents>true</CollectSampleEvents>  
    <CollectGpuEvents>true</CollectGpuEvents>  
    <CollectFileIO>true</CollectFileIO>  
  </FilterConfig>  

  <UserBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </UserBufferSettings>  

  <KernelBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </KernelBufferSettings>  

  <!-- List of MyCodeDirectory directories -->  
  <JustMyCode>  
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>  
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>  
  </JustMyCode>  
</LocalConfig>  

```
