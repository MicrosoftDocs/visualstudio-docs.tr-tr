---
title: Vsınstr uyarıları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a306276e015d06fe3becf297d0bb5834f640a1a7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571652"
---
# <a name="vsinstr-warnings"></a>Vsınstr uyarıları
Aşağıdaki tabloda tarafından verilen uyarılar *VSInstr.exe* aracı. Görünmesini gizlemek için uyarı numaralarını NOWARN seçeneğiyle kullanabilirsiniz.  
  
|Uyarı sayısı|Açıklama|  
|--------------------|-----------------|  
|**VSP2000**|İç Hata. Bu çalıştırılabilir için modül dosya adı alınamıyor.|  
|**VSP2001**|\<derleme adı > kesin adlandırılmış bir derlemedir. Bunu yürütülebilmesi yeniden imzalanmış olmalıdır.<br /><br /> Bu uyarı, imzalı bir derleme izlenmiş oluşur. Kullanabileceğiniz *sn.exe* aracı ikili çekilmeye veya geçici olarak devre dışı güçlü ad gereksinim kapatmak için. Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)](/dotnet/framework/tools/sn-exe-strong-name-tool).|  
|**VSP2002**|İşlevi bulunamadı \<funcname > dosyasındaki \<dosya adı ><br /><br /> Bir işlev içinde belirtilen dosya bulunamıyorsa bu uyarıyı oluşur.|  
|**VSP2003**|Herhangi bir işlev atlar çapraz bulunamadı \<funcname > dosyasındaki \<dosyaadı >.<br /><br /> Vsınstr iptal edilmez edilemez, bu uyarıyı arası atlar ortaya çıkar. Çapraz atlama kodu iyileştirme için kullanılır.|  
|**VSP2004**|İşlev \<funcname > DIŞLAMA komut satırı anahtarını kullanarak hariç tutuldu ancak çapraz atlama içerdiğinden gerekli.<br /><br /> Bu uyarı işlevi hariç TUTMA seçeneğini kullanarak hariç tutuldu ancak izleme işlemi sırasında gerekli oluşur. Profil Oluşturucu otomatik olarak gerekli işlevi içerir.|  
|**VSP2005**|İç işaretleme hatası \<hata metni ><br /><br /> İzleme gerçekleştirdiyseniz, bu uyarı görüntülenir. Bunu düzeltilebilir olup olmadığını belirlemek için hata metni gözden geçirin.|  
|**VSP2006**|PDB için bulamadı \<adı ><br /><br /> Bu uyarı PDB dosyası üzerinde arama yolu yok veya ikili eşleşmiyor oluşur.|  
|**VSP2007**|\<Dosya adı > instrumentable kod içerir.<br /><br /> Bu uyarı, ikili dosya işlevlerde tüm dışlanan veya belirtilen dosya yalnızca kaynakları içeriyorsa görüntülenir.|  
|**VSP2008**|Güvenlik öznitelikleri alınamıyor \<adı >. Hata kodu \<kodu ><br /><br /> Kullanıcı READ_DAC iznine sahip değilse bu uyarı oluşur. İkili için özgün DACL korumak profil oluşturucu izleme işlemi sırasında çalışır. Özgün ikili ile yeni bir ikili değiştirilir olduğundan, özgün ikili DACL kopyalanır ve yeni ikili uygulanır. Bu kullanıcı özgün ikili READ_DAC erişimi yoksa başarısız olabilir.|  
|**VSP2009**|Güvenlik öznitelikleri ayarlanamıyor \<adı >. Hata kodu \<hata numarası ><br /><br /> Kullanıcı WRITE_DAC iznine sahip değilse bu uyarı oluşur. İkili için özgün DACL korumak profil oluşturucu izleme işlemi sırasında çalışır. Özgün ikili ile yeni bir ikili değiştirilir olduğundan, özgün ikili DACL kopyalanır ve yeni ikili uygulanır. Bu kullanıcı yeni ikili WRITE_DAC erişimi yoksa başarısız olabilir.|  
|**VSP2010**|Hiçbir işlevlerdir özellikle nedeniyle dosyaların - için seçilen /-EXCLUDE seçenekleri içerir|  
|**VSP2011**|Funcspec dahil etme/hariç tutma \<adı > Tüm İşlevler eşleşmiyor.|  
|**VSP2012**|Görüntü için kod kapsamı izlenmiş herhangi bir kod içermiyor.<br /><br /> Profil Oluşturucu kodu aşağıdaki türde izleme değil:<br /><br /> -Statik CRT işlevleri<br />-İle NonUserCodeAttribute öznitelikli yönetilen yöntemleri<br />-İle DebuggerHiddenAttribute öznitelikli yönetilen yöntemleri<br />-MASM blokları<br /><br /> Bu filtreleme sonrasında, varsa, sol herhangi bir kodu bu uyarı oluşturulur.|  
|**VSP2013**|Bu görüntüyü bir 32 bitlik işlem olarak çalışmasını gerektirir. CLR üstbilgi bayrakları bu yansıtacak şekilde güncelleştirildi.<br /><br /> Profil Oluşturucu ikili 64-bit işletim sistemlerinin 32 bit işlem WOW64 öykünücüsünde açabilirsiniz şekilde değiştirir. Varolan bir 64-bit işlemde yüklenen kitaplıklarını (DLL'ler) bu başarısız olabilir. Bu uyarı bağımlılığın kullanıcıyı uyarır.|  
|**VSP2014**|Sonuçta elde edilen izleme eklenmiş görüntü geçersiz olduğu belirlendi ve çalışmayabilir.<br /><br /> Bu ileti, geçersiz bir PE üstbilgi son Araçlı derleme sahip oluşur.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSInstr](../profiling/vsinstr.md)