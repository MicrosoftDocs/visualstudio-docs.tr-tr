---
title: Desteklenen kod değişiklikleri (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C# language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C#], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c1d4333014f63bec73c13b3a7b1d5f9c7d59697f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854123"
---
# <a name="supported-code-changes-c"></a>Desteklenen Kod Değişiklikleri (C++)
Düzenle ve devam et Visual C++ için kod değişiklikleri çoğu türde işler. Ancak, bazı değişiklikler, program yürütme sırasında uygulanamaz. Bu değişiklikleri uygulamak için yürütmeyi durdurun ve kodu yeni bir sürümünü oluşturun.  
  
 Bkz: [Düzenle ve devam et (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) Visual Studio'da C++ için Düzenle ve devam et ile çalışma hakkında bilgi.  
  
##  <a name="BKMK_Unsupported_changes"></a> Desteklenmeyen değişiklikleri  
 Aşağıdaki değişiklikler C/C++ hata ayıklama oturumu sırasında uygulanamaz:  
  
- Genel veya statik veri çoğu geçer.  
  
- Başka bir makineden kopyalanır ve yerel olarak yerleşik olmayan yürütülebilir yapılan değişiklikler.  
  
- Bir sınıfın veri üyelerine gibi bir nesne düzenini etkileyen değişiklikler için veri türü.  
  
- Yeni kod veya veri fazla 64 k bayt ekleniyor.  
  
- Yönerge işaretçisi önce bir noktada bir oluşturucu gerektiren değişkenleri ekleniyor.  
  
- Çalışma zamanı başlatma gerektiren kod etkileyen değişiklikler.  
  
- Özel durum işleyicileri, bazı durumlarda ekleniyor.  
  
- Kaynak dosyalarda yapılan değişiklikler.  
  
- Salt okunur dosyaları kodunda yapılan değişiklikler.  
  
- Kod karşılık gelen bir PDB dosyası olmadan yapılan değişiklikler.  
  
- Nesne dosyası sahip kod değişiklikleri.  
  
  Bu değişikliklerden birini yapın ve ardından kod değişikliklerini uygulamayı deneyin, hata veya uyarı iletisi görünür **çıkış** penceresi.  
  
- Düzenle ve devam et, statik kitaplıklar güncelleştirilmez. Statik kitaplıkta bir değişiklik yaparsanız, eski sürümü ile yürütme devam eder ve herhangi bir uyarı verilir.  
  
##  <a name="BKMK_Unsupported_scenarios"></a> Desteklenmeyen senaryolar  
 Düzenle ve devam et C/C++ için hata ayıklama aşağıdaki senaryolarda kullanılabilir:  
  
-   Hata ayıklama ile derlenen yerel uygulamalar [/Zo (geliştirmek için iyileştirilmiş hata ayıklama)](/cpp/build/reference/zo-enhance-optimized-debugging)  
  
-   Visual Studio 2015 güncelleştirme UWP uygulamaları veya bileşenleri hata ayıklama 1, önceki Visual Studio sürümlerinde. Artık desteklediği için Visual Studio 2015 güncelleştirme 1'de başlayarak, Düzenle ve devam et DirectX uygulamaları, C++ UWP uygulamaları ile kullanabileceğiniz `/ZI` derleyici anahtarıyla `/bigobj` geçin. Düzenleme da kullanabilirsiniz ve ikili dosyalarla devam et ile derlenmiş olan `/FASTLINK` geçin.  
  
-   Windows 98'hata ayıklama.  
  
-   Karma mod (yerel/yönetilen) hata ayıklama.  
  
-   JavaScript hata ayıklama.  
  
-   SQL hata ayıklama.  
  
-   Bir döküm dosyası hata ayıklama.  
  
-   İşlenmeyen bir özel durumdan sonra kod düzenleme, **işlenmemiş özel durumlarda çağrı yığınını geriye doğru izleme** seçeneği belirlenmez.  
  
-   Bir uygulama kullanarak hata ayıklama **ekleme** seçerek uygulamayı çalıştırmak yerine **Başlat** üzerinde **hata ayıklama** menüsü.  
  
-   En iyi duruma getirilmiş kodda hata ayıklama.  
  
-   Derleme hataları nedeniyle oluşturmak yeni bir sürüm başarısız olduktan sonra kodunuzu eski bir sürümü hata ayıklama.  
  
##  <a name="BKMK_Linking_limitations"></a> Bağlama sınırlamaları  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Düzenle ve Devam Et'i devre dışı bırakan bağlayıcı seçenekleri  
 Aşağıdaki bağlayıcı Seçenekleri Düzenle ve Devam Et'i devre dışı bırakın:  
  
-   Ayarı **/OPT: ref**, **/OPT: ICF**, veya **/Incremental: No** devre dışı bırakır, Düzenle ve devam şu uyarıyı vererek:  
  
     BAĞLANTI: Uyarısı LNK4075: / edıtandcontınue OPT nedeniyle yoksayılıyor  
  
     belirtim  
  
-   Ayarı **/sipariş**, **/yayın**, veya **/FORCE** devre dışı bırakır, Düzenle ve devam etmek bu uyarı ile:  
  
     BAĞLANTI: Uyarısı LNK4075: / Incremental, / OPTION nedeniyle yoksayılıyor  
  
     belirtim  
  
-   Herhangi bir seçenek ayarı devre dışı Düzenle ve devam herhangi belirli bir uyarı ile bir program veritabanı (.pdb) dosyası oluşturulmasını engeller.  
  
###  <a name="BKMK_Auto_relinking_limitations"></a> Otomatik yeniden bağlantılandırmayı sınırlamaları  
 Varsayılan olarak, Düzenle ve devam et i programınızı güncel yürütülebilir bir dosya oluşturmak için hata ayıklama oturumu sonunda.  
  
 Orijinal derleme konumu dışında bir konumdan ayıkladığınız, Düzenle ve devam et programınızı yeniden kullanılamaz. Bir ileti el ile yeniden oluşturmanız gerektiğini bildirir.  
  
 Düzenle ve devam et değil yeniden statik kitaplıklar. Düzenle ve Devam Et'i kullanmadan bir statik kitaplığa değişiklik yaparsanız, onu kullanarak kitaplık ve yeniden bağlama uygulamaları el ile yeniden oluşturmanız gerekir.  
  
 Düzenle ve devam et çağrılamadı özel derleme adımları. Özel derleme adımları, programınızın kullanıyorsa, özel derleme adımları etkinleştirilebilir böylece, el ile yeniden isteyebilirsiniz. Bu durumda, el ile yeniden oluşturmanız istenir emin olmak için Düzenle ve devam et sonra yeniden bağlantılandırmayı devre dışı bırakabilirsiniz.  
  
 **Düzenle ve devam et sonra yeniden bağlantılandırmayı devre dışı bırakmak için**  
  
1.  Üzerinde **hata ayıklama** menüsünde seçin **seçenekler ve ayarlar**.  
  
2.  İçinde **seçenekleri** iletişim kutusunun **hata ayıklama** düğüm ve select **Düzenle ve devam et** düğümü.  
  
3.  NET **kod değişikliklerini hata ayıklama sonrasında yeniden Bağla** onay kutusu.  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a> Önceden derlenmiş başlık sınırlamaları  
 Varsayılan olarak, düzenleyin ve yükler ve işlemleri önceden derlenmiş üst bilgiler kod değişikliklerinin işlemleri hızlandırmak için arka planda devam edin. Önceden derlenmiş üst bilgiler yüklenirken bir makinede sınırlı RAM ile derleme yapıyorsanız, bir sorun olabilir, fiziksel bellek ayırma gerektirir. Bu sorun, hata ayıklama sırasında kullanılabilir fiziksel bellek miktarını belirlemek için Windows Görev Yöneticisi'ni kullanarak olabilir, belirleyebilirsiniz. Bu miktar, önceden derlenmiş üst bilgilerin boyutundan daha büyük ise, Düzenle ve devam et hiç sorun değil olmalıdır. Tutar, önceden derlenmiş üst bilgilerin boyuttan daha az ise, arka planda önceden derlenmiş üst bilgiler yüklenmesini Düzenle ve devam et engelleyebilirsiniz.  
  
 **Düzenle ve devam et için arka plan önceden derlenmiş üstbilgilerin yüklenmesini devre dışı bırakmak için**  
  
1.  Üzerinde **hata ayıklama** menüsünde seçin **seçenekler ve ayarlar**.  
  
2.  İçinde **seçenekleri** iletişim kutusunun **hata ayıklama** düğüm ve select **Düzenle ve devam et** düğümü.  
  
3.  NET **izin önceden derleme** onay kutusu.  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a> IDL öznitelik sınırlamaları  
 Düzenle ve devam et değil yeniden arabirim tanımı (IDL) dosyaları. Bu nedenle, hata ayıklama sırasında IDL öznitelikleri değişiklikler yansıtılmaz. IDL öznitelikleri için değişiklik sonucunu görmek için hata ayıklamayı durdurmak ve uygulamanızı yeniden oluşturun. Düzenle ve devam et oluşturmaz bir hata veya uyarı IDL öznitelikleri değiştirdiyseniz. Daha fazla bilgi için [IDL öznitelikleri](/cpp/windows/idl-attributes).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenle ve Devam Et (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)