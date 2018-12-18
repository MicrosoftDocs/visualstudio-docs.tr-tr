---
title: MT görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9b14de0b9e80379736dd7f6a02cb374d475fcda
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214948"
---
# <a name="mt-task"></a>MT Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Microsoft bildirim aracı, sarmalar mt.exe. Daha fazla bilgi için "Mt.exe" bakın [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır **MT** görev. Çoğu görev parametreleri ve parametrelerin birkaç kümeleri bir komut satırı seçeneğine karşılık gelir.  
  
> [!NOTE]
>  Bir tire mt.exe belgeleri kullanır (**-**) komut satırı seçenekleri, ancak bu konu için ön ek bir eğik çizgi kullanır (**/**). Ya da kabul edilebilir önekidir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|İsteğe bağlı **String []** parametresi.<br /><br /> Bir veya daha fazla bildirim dosyalarının adını belirtir.<br /><br /> Daha fazla bilgi için **/MANIFEST** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi. Örneğin, "*/option1 /option2 /option#*". Diğer tarafından temsil edilmez komut satırı seçeneklerini belirtmek için bu parametreyi kullanın **MT** görev parametresi.<br /><br /> Daha fazla bilgi için "Mt.exe" bakın [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**assemblyIdentity**|İsteğe bağlı **dize** parametresi.<br /><br /> Öznitelik değerleri belirtir **assemblyIdentity** bildirimin öğesi. İlk bileşen değeri olduğu bir virgülle ayrılmış listesini belirtin `name` özniteliği, formu içeren bir veya daha fazla ad/değer çiftleri tarafından izlenen  *\<öznitelik adı > = < attribute_value >*.<br /><br /> Daha fazla bilgi için **/identity** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**ComponentFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> .Rgs veya .tlb dosyalarından oluşturmak istediğiniz dinamik bağlantı kitaplığının adını belirtir. Bu parametreyi belirtirseniz gereklidir **RegistrarScriptFile** veya **TypeLibraryFile** MT görevi parametreleri.<br /><br /> Daha fazla bilgi için **/dll** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**DependencyInformationFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirim aracına ait derleme bağımlılık bilgilerini izlemek için Visual Studio tarafından kullanılan bağımlılık bilgi dosyasını belirtir.|  
|**EmbedManifest**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bildirim dosyası derlemeye gömer. Varsa `false`, tek başına bir bildirim dosyası oluşturur.|  
|**EnableDPIAwareness**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, uygulamayı DPI kullanan olarak işaretleyen bildirim bilgileri ekler. DPI kullanan uygulama yazma, çok çeşitli yüksek DPI görüntü ayarları arasında tutarlı bir şekilde iyi görünen bir kullanıcı arabirimi sağlar.<br /><br /> Daha fazla bilgi için "Yüksek DPI" bakın [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**GenerateCatalogFiles**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, katalog tanımı (.cdf) dosyaları oluşturur.<br /><br /> Daha fazla bilgi için **/makecdfs** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**GenerateCategoryTags**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, Kategori etiketlerinin oluşturulmasını sağlar. Bu parametre `true`, **ManifestFromManagedAssemblyMT** görev parametresi de belirtilmelidir.<br /><br /> Daha fazla bilgi için **/Category** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**InputResourceManifests**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir belirtilen tanımlayıcıya sahip rt_manıfest türü kaynağı bildirim girişi. Formunun bir kaynak belirtin  _\<Dosya > [_**;** _[_**#**_] < resource_id >]_, isteğe bağlı `resource_id` parametresi, negatif olmayan, 16-bit bir sayı.<br /><br /> Hayır ise `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değeri (1) kullanılır.<br /><br /> Daha fazla bilgi için **/inputresource** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**ManifestFromManagedAssembly**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen yönetilen derlemeden bir bildirim oluşturur.<br /><br /> Daha fazla bilgi için **/managedassemblyname** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**ManifestToIgnore**|İsteğe bağlı **dize** parametresi.<br /><br /> (Kullanılmıyor.)|  
|**OutputManifestFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıkış bildirimi adını belirtir. Bu parametre atlanırsa ve yalnızca bir bildirim üzerinde işlem yapılan, bu bildirim bir yerde değiştirildi.<br /><br /> Daha fazla bilgi için **/out** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**OutputResourceManifests**|İsteğe bağlı **dize** parametresi.<br /><br /> Bir belirtilen tanımlayıcıya sahip rt_manıfest türü kaynağı bildirim çıkışı. Kaynak, biçimindedir  _\<Dosya > [_**;** _[_**#**_] < resource_id >]_, isteğe bağlı `resource_id` parametresi, negatif olmayan, 16-bit bir sayı.<br /><br /> Hayır ise `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değeri (1) kullanılır.<br /><br /> Daha fazla bilgi için **/outputresource** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**RegistrarScriptFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kayıtsız COM bildirim desteği için kullanılacak Kaydedici betik (.rgs) dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için **/rgs** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**ReplacementsFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaydedici betik (.rgs) dosyasını değiştirilebilir dizelerin değerlerini içeren dosyayı belirtir.<br /><br /> Daha fazla bilgi için **/replacements** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi proje çıkışına katıştırmak için kullanılan çıkış kaynakları dosyasını belirtir.|  
|**Kaynakları**|İsteğe bağlı `ITaskItem[]` parametresi.<br /><br /> Bildirim kaynak dosyaları boşlukla ayrılmış listesini belirtir.<br /><br /> Daha fazla bilgi için **/MANIFEST** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**SuppressDependencyElement**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bağımlılık öğeler olmadan bir bildirim oluşturur. Bu parametre `true`, ayrıca belirtin **ManifestFromManagedAssemblyMT** görev parametresi.<br /><br /> Daha fazla bilgi için **/nodependency** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**SuppressStartupBanner**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için **/nologo** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**TrackerLogDirectory**|İsteğe bağlı `String` parametresi.<br /><br /> Bu görev için izleme günlüklerinin depolandığı Ara dizini belirtir.|  
|**TypeLibraryFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Tür kitaplığı (.tlb) dosyasının adını belirtir. Bu parametreyi belirtirseniz, aynı zamanda belirtin **ComponentFileNameMT** görev parametresi.<br /><br /> Daha fazla bilgi için **/TLB** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
|**UpdateFileHashes**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, dosyaları tarafından belirtilen yolda karma değerini hesaplar **UpdateFileHashesSearchPathMT** görev parametresi ve değerini güncelleştirir. **karma** özniteliği**dosya** hesaplanan değeri kullanarak bildirimin öğesi.<br /><br /> Daha fazla bilgi için **/hashupdate** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi. Ayrıca bkz: **UpdateFileHashesSearchPath** bu tablodaki parametresi.|  
|**UpdateFileHashesSearchPath**|İsteğe bağlı `String` parametresi.<br /><br /> Dosya karmalarının güncellenmesinin kullanılacak arama yolunu belirtir. İle bu parametreyi kullanın **UpdateFileHashesMT** görev parametresi.<br /><br /> Daha fazla bilgi için **UpdateFileHashes** bu tablodaki parametresi.|  
|**VerboseOutput**|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, ayrıntılı hata ayıklama bilgilerini görüntüler.<br /><br /> Daha fazla bilgi için **/ verbose** "Mt.exe içinde" seçeneğini [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web sitesi.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



