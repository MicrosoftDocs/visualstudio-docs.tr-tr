---
title: MT görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6e4298fa9482674232dea2cae98bb25ba51be30
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219880"
---
# <a name="mt-task"></a>MT görevi
Microsoft bildirim aracı, sarmalar *mt.exe*. Daha fazla bilgi için [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **MT** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
> [!NOTE]
>  *Mt.exe* belgeler kullanan bir tire (**-**) komut satırı seçenekleri, ancak bu konu için ön ek bir eğik çizgi kullanır (**/**). Ya da kabul edilebilir önekidir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|İsteğe bağlı **String []** parametresi.<br /><br /> Bir veya daha fazla bildirim dosyalarının adını belirtir.<br /><br /> Daha fazla bilgi için **/MANIFEST** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi. Örneğin, /\<Seçenek1 > /\<Seçenek2 > /\<seçeneği #>. Diğer tarafından temsil edilmez komut satırı seçeneklerini belirtmek için bu parametreyi kullanın **MT** görev parametresi.<br /><br /> Daha fazla bilgi için [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**assemblyIdentity**|İsteğe bağlı **dize** parametresi.<br /><br /> Öznitelik değerleri belirtir **assemblyIdentity** bildirimin öğesi. İlk bileşen değeri olduğu bir virgülle ayrılmış listesini belirtin `name` özniteliği, formu içeren bir veya daha fazla ad/değer çiftleri tarafından izlenen  *\<öznitelik adı > = < attribute_value >*.<br /><br /> Daha fazla bilgi için **/identity** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ComponentFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Yapıdan düşündüğünüz dinamik bağlantı kitaplığının adı belirtir *.rgs* veya *.tlb* dosyaları. Bu parametreyi belirtirseniz gereklidir **RegistrarScriptFile** veya **TypeLibraryFile** MT görevi parametreleri.<br /><br /> Daha fazla bilgi için **/dll** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**DependencyInformationFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirim aracına ait derleme bağımlılık bilgilerini izlemek için Visual Studio tarafından kullanılan bağımlılık bilgi dosyasını belirtir.|  
|**EmbedManifest**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bildirim dosyası derlemeye gömer. Varsa `false`, tek başına bir bildirim dosyası oluşturur.|  
|**EnableDPIAwareness**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, uygulamayı DPI kullanan olarak işaretleyen bildirim bilgileri ekler. DPI kullanan uygulama yazma, çok çeşitli yüksek DPI görüntü ayarları arasında tutarlı bir şekilde iyi görünen bir kullanıcı arabirimi sağlar.<br /><br /> Daha fazla bilgi için [yüksek DPI](https://docs.microsoft.com/windows/desktop/win7devguide/high-dpi).|  
|**GenerateCatalogFiles**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, kataloğu tanımı oluşturur (*.cdf*) dosyaları.<br /><br /> Daha fazla bilgi için **/makecdfs** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**GenerateCategoryTags**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, Kategori etiketlerinin oluşturulmasını sağlar. Bu parametre `true`, **ManifestFromManagedAssemblyMT** görev parametresi de belirtilmelidir.<br /><br /> Daha fazla bilgi için **/Category** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**InputResourceManifests**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir belirtilen tanımlayıcıya sahip rt_manıfest türü kaynağı bildirim girişi. Formunun bir kaynak belirtin \<Dosya > [; [ #]\<resource_id >], isteğe bağlı \<resource_id > parametresi, negatif olmayan, 16-bit bir sayı.<br /><br /> Hayır ise `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değeri (1) kullanılır.<br /><br /> Daha fazla bilgi için **/inputresource** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ManifestFromManagedAssembly**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen yönetilen derlemeden bir bildirim oluşturur.<br /><br /> Daha fazla bilgi için **/managedassemblyname** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ManifestToIgnore**|İsteğe bağlı **dize** parametresi.<br /><br /> (Kullanılmıyor.)|  
|**OutputManifestFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıkış bildirimi adını belirtir. Bu parametre atlanırsa ve yalnızca bir bildirim üzerinde işlem yapılan, bu bildirim bir yerde değiştirildi.<br /><br /> Daha fazla bilgi için **/out** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**OutputResourceManifests**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir belirtilen tanımlayıcıya sahip rt_manıfest türü kaynağı bildirim çıkışı. Kaynak, biçimindedir \<Dosya > [; [ #]\<resource_id >], isteğe bağlı \<resource_id > parametresi, negatif olmayan, 16-bit bir sayı.<br /><br /> Hayır ise `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değeri (1) kullanılır.<br /><br /> Daha fazla bilgi için **/outputresource** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**RegistrarScriptFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaydedici betik adını belirtir (*.rgs*) kayıt gerektirmeyen COM bildirim desteği için kullanılacak dosya.<br /><br /> Daha fazla bilgi için **/rgs** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ReplacementsFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaydedici betik değiştirilebilir dizelerin değerlerini içeren dosyayı belirtir (*.rgs*) dosyası.<br /><br /> Daha fazla bilgi için **/replacements** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi proje çıkışına katıştırmak için kullanılan çıkış kaynakları dosyasını belirtir.|  
|**Kaynakları**|İsteğe bağlı `ITaskItem[]` parametresi.<br /><br /> Bildirim kaynak dosyaları boşlukla ayrılmış listesini belirtir.<br /><br /> Daha fazla bilgi için **/MANIFEST** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**SuppressDependencyElement**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bağımlılık öğeler olmadan bir bildirim oluşturur. Bu parametre `true`, ayrıca belirtin **ManifestFromManagedAssemblyMT** görev parametresi.<br /><br /> Daha fazla bilgi için **/nodependency** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**SuppressStartupBanner**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için **/nologo** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**TrackerLogDirectory**|İsteğe bağlı `String` parametresi.<br /><br /> Bu görev için izleme günlüklerinin depolandığı Ara dizini belirtir.|  
|**TypeLibraryFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Tür kitaplığının adını belirtir (*.tlb*) dosyası. Bu parametreyi belirtirseniz, aynı zamanda belirtin **ComponentFileNameMT** görev parametresi.<br /><br /> Daha fazla bilgi için **/TLB** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**UpdateFileHashes**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, dosyaları tarafından belirtilen yolda karma değerini hesaplar **UpdateFileHashesSearchPathMT** görev parametresi ve değerini güncelleştirir. **karma** özniteliği**dosya** hesaplanan değeri kullanarak bildirimin öğesi.<br /><br /> Daha fazla bilgi için **/hashupdate** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe). Ayrıca bkz: **UpdateFileHashesSearchPath** bu tablodaki parametresi.|  
|**UpdateFileHashesSearchPath**|İsteğe bağlı `String` parametresi.<br /><br /> Dosya karmalarının güncellenmesinin kullanılacak arama yolunu belirtir. İle bu parametreyi kullanın **UpdateFileHashesMT** görev parametresi.<br /><br /> Daha fazla bilgi için **UpdateFileHashes** bu tablodaki parametresi.|  
|**VerboseOutput**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, ayrıntılı hata ayıklama bilgilerini görüntüler.<br /><br /> Daha fazla bilgi için **/ verbose** seçeneğini [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)