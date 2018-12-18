---
title: MSBuild görev başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 790d3e788fb04351fc379e8a4205e802c58516ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951151"
---
# <a name="msbuild-task-reference"></a>MSBuild görev başvurusu
Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevleri aşağıdaki listede bulunan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Zaman [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] yüklenen, ek görevler oluşturmak için kullanılan olan [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projeleri. Daha fazla bilgi için [Visual C++ görevleri](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  

 Bu bölümdeki konular, listelenen parametrelerin yanı sıra, her görev, ayrıca aşağıdaki parametrelere sahiptir:  


| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametresi.<br /><br /> A `Boolean` ifade eden [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altyapısı bu görevi yürüten olup olmadığını belirlemek için kullanır. Tarafından desteklenen koşullar hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], bkz: [koşullar](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, sonraki görevlerinde [hedef](../msbuild/target-element-msbuild.md) öğesi ile derleme devam yürütülecek ve görevin tüm hataları uyarı olarak kabul edilir.<br />-   **ErrorAndContinue**. Bir görev başarısız olduğunda, sonraki görevlerinde `Target` öğesi ile derleme devam yürütmek ve tüm hataları görev hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, listesindeki kalan görevlere `Target` olmayan öğe ve derleme yürütülür ve tüm `Target` öğesi ve yapı başarısız olduğu değerlendirilir.<br /><br /> .NET Framework 4.5 yalnızca desteklenen önce sürümleri `true` ve `false` değerleri.<br /><br /> Daha fazla bilgi için [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Bu bölümde  
 [Görev taban sınıfı](../msbuild/task-base-class.md)  
 Öğesinden türetilen görevleri birkaç parametre ekler <xref:Microsoft.Build.Utilities.Task> sınıfı.  

 [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md)  
 Öğesinden türetilen görevleri birkaç parametre ekler <xref:Microsoft.Build.Tasks.TaskExtension> sınıfı.  

 [ToolTaskExtension taban sınıfı](../msbuild/tooltaskextension-base-class.md)  
 Öğesinden türetilen görevleri birkaç parametre ekler <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfı.  

 [AL (derleme bağlayıcı) görevi](../msbuild/al-assembly-linker-task.md)  
 Bir modül olan bir veya daha fazla veya kaynak dosyalar bildiriminden bir derleme oluşturur.  

 [AspNetCompiler görevi](../msbuild/aspnetcompiler-task.md)  
 Sarmalar *aspnet_compiler.exe*, ASP.NET uygulamalarının önceden derlemek için bir yardımcı program.  

 [AssignCulture görevi](../msbuild/assignculture-task.md)  
 Kültür tanımlayıcıları öğesine atar.  

 [AssignProjectConfiguration görevi](../msbuild/assignprojectconfiguration-task.md)  
 Yapılandırma dizeleri listesini kabul eder ve bunları belirtilen projelere atar.  

 [AssignTargetPath görevi](../msbuild/assigntargetpath-task.md)  
 Dosyaların bir listesini kabul eder ve ekler `<TargetPath>` zaten belirtilmezse, öznitelikleri.  

 [CallTarget görevi](../msbuild/calltarget-task.md)  
 Bir hedef proje dosyasındaki çağırır.  

 [CombinePath görevi](../msbuild/combinepath-task.md)  
 Belirtilen yolu tek yola birleştirir.  

 [ConvertToAbsolutePath görevi](../msbuild/converttoabsolutepath-task.md)  
 Bir göreli yol veya başvuru bir mutlak yola dönüştürür.  

 [Kopyalama görevi](../msbuild/copy-task.md)  
 Dosyaları yeni bir konuma kopyalar.  

 [CreateCSharpManifestResourceName görevi](../msbuild/createcsharpmanifestresourcename-task.md)  
 Oluşturur bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-stili bildirim adından bir verilen *.resx* dosya adı veya diğer kaynak.  

 [CreateItem görevi](../msbuild/createitem-task.md)  
 Girdi öğelerinin öğeleri bir listeden diğerine kopyalanmasına izin verme, öğe koleksiyonlarını doldurur.  

 [CreateProperty görevi](../msbuild/createproperty-task.md)  
 Bir özellik veya dize diğerine kopyalanması için değerler sağlayan giriş değerleri özelliklerinden doldurur.  

 [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Oluşturur bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-stili bildirim adından bir verilen *.resx* dosya adı veya diğer kaynak.  

 [CSC görevi](../msbuild/csc-task.md)  
 Yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modüllerini oluşturmak için Visual C# derleyicisini çağırır.  

 [Silme görevi](../msbuild/delete-task.md)  
 Belirtilen dosyaları siler.  

 [DownloadFile görevi](../msbuild/downloadfile-task.md)  
 Bir dosya belirtilen konuma indirir.  

 [Hata görevi](../msbuild/error-task.md)  
 Bir derleme durdurur ve değerlendirilen bir koşullu ifadeye göre bir hatayı günlüğe kaydeder.  

 [Yürütme görevi](../msbuild/exec-task.md)  
 Belirtilen bağımsız değişkenlerle belirtilen program veya komut çalıştırır.  

 [FindAppConfigFile görevi](../msbuild/findappconfigfile-task.md)  
 Bulur *app.config* dosya varsa sağlanan listeler.  

 [Findınlist görevi](../msbuild/findinlist-task.md)  
 Eşleşen öğebelirtimi belirtilen bir listede bir öğe bulur.  

 [FindUnderPath görevi](../msbuild/findunderpath-task.md)  
 Belirtilen öğe koleksiyonunda öğelerin belirtilen klasörde ve alt klasörlerindeki tüm mevcut belirler.  

 [FormatUrl görevi](../msbuild/formaturl-task.md)  
 Bir URL doğru bir URL biçimine dönüştürür.  

 [FormatVersion görevi](../msbuild/formatversion-task.md)  
 Düzeltme numarası için sürüm numarası ekler.  

 [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)  
 Oluşturur bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi ya da yerel bir bildirim.  

 [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md)  
 Algılama, indirmek ve bir uygulama ve önkoşulları yüklemek için otomatik bir yol sağlar.  

 [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)  
 Oluşturur bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi.  

 [GenerateResource görevi](../msbuild/generateresource-task.md)  
 Dönüştürür *.txt* ve *.resx* ortak dil çalışma zamanı ikili dosyalarını *.resources* dosyaları.  

 [Generatetrustınfo görevi](../msbuild/generatetrustinfo-task.md)  
 Uygulama güvenini taban bildirimini ve gelen oluşturur `TargetZone` ve `ExcludedPermissions` parametreleri.  

 [Getassemblyıdentity görevi](../msbuild/getassemblyidentity-task.md)  
 Belirtilen dosyalardan derleme kimlikleri alır ve kimlik bilgilerini çıkarır.  

 [GetFrameworkPath görevi](../msbuild/getframeworkpath-task.md)  
 Yolunu alır [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] derlemeler.  

 [GetFrameworkSdkPath görevi](../msbuild/getframeworksdkpath-task.md)  
 Yolunu alır [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  

 [GetReferenceAssemblyPaths görevi](../msbuild/getreferenceassemblypaths-task.md)  
 Başvuru bütünleştirilmiş kodu yolları çeşitli çerçevesini döndürür.  

 [LC görevi](../msbuild/lc-task.md)  
 Oluşturur bir *.license* dosyasını bir *.licx* dosya.  

 [MakeDir görevi](../msbuild/makedir-task.md)  
 Dizin oluşturur ve gerekirse, tüm üst dizinleri.  

 [İleti görevi](../msbuild/message-task.md)  
 Derleme sırasında bir ileti kaydeder.  

 [Taşıma görevi](../msbuild/move-task.md)  
 Dosyalarını yeni konuma taşır.  

 [MSBuild görevi](../msbuild/msbuild-task.md)  
 Yapılar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] başka projelerden [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje.  

 [ReadLinesFromFile görevi](../msbuild/readlinesfromfile-task.md)  
 Öğe listesini bir metin dosyasından okur.  

 [RegisterAssembly görevi](../msbuild/registerassembly-task.md)  
 Belirtilen derleme içindeki meta veriyi okur ve kayıt defterine gerekli girişleri ekler.  

 [RemoveDir görevi](../msbuild/removedir-task.md)  
 Belirtilen dizinlerin ve tüm alt dizinleri ve dosyaları kaldırır.  

 [RemoveDuplicates görevi](../msbuild/removeduplicates-task.md)  
 Yinelenen öğeleri belirtilen öğeyi koleksiyondan kaldırır.  

 [RequiresFramework35SP1Assembly görevi](../msbuild/requiresframework35sp1assembly-task.md)  
 Uygulama .NET Framework 3.5 SP1 isteyip istemediğini belirler.  

 ResGen görevi  
 Kullanımdan kalktı. Kullanım [GenerateResource görevi](../msbuild/generateresource-task.md) dönüştürmek için görev *.txt* ve *.resx* ortak dil çalışma zamanı ikili dosyaları *.resources* dosyaları.  

 [ResolveAssemblyReference görevi](../msbuild/resolveassemblyreference-task.md)  
 Belirtilen derlemelerini bağımlı derlemelerin belirler.  

 [ResolveComReference görevi](../msbuild/resolvecomreference-task.md)  
 Liste bir veya daha fazla türdeki kitaplık adlarını alır veya *.tlb* dosyaları ve disk üzerindeki konumlara bu tür kitaplıklarını giderir.  

 [ResolveKeySource görevi](../msbuild/resolvekeysource-task.md)  
 Tanımlayıcı ad anahtar kaynağını belirler  

 [ResolveManifestFiles görevi](../msbuild/resolvemanifestfiles-task.md)  
 Yapı işleminde aşağıdaki öğeleri için bildirim üretme dosyaları giderir: öğe, bağımlılıkları, Uyduları, içerik, hata ayıklama sembolleri ve belgeleri yerleşik.  

 [ResolveNativeReference görevi](../msbuild/resolvenativereference-task.md)  
 Yerel başvurular çözümleniyor.  

 [ResolveNonMSBuildProjectOutput görevi](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 MSBuild dışındaki proje başvuruları için çıkış dosyalarının belirler.  

 [SGen görevi](../msbuild/sgen-task.md)  
 Bir XML serileştirme derleme türleri için belirtilen derlemesinde oluşturur.  

 [SignFile görevi](../msbuild/signfile-task.md)  
 Belirtilen dosyayı belirtilen sertifikayı kullanarak imzalar.  

 [Dokunma görevi](../msbuild/touch-task.md)  
 Dosya erişim ve değişiklik saatlerini ayarlar.  

 [UnregisterAssembly görevi](../msbuild/unregisterassembly-task.md)  
 Belirtilen derlemeleri COM birlikte çalışma amacıyla kaydını siler.  

 [Görev sıkıştırmasını açın](../msbuild/unzip-task.md)  
 Unzips bir *.zip* belirtilen konuma arşiv.

 [UpdateManifest görevi](../msbuild/updatemanifest-task.md)  
 Bir bildirimdeki seçili özelliklerini güncelleştirir ve Çekildi.  

 [Vbc görevi](../msbuild/vbc-task.md)  
 Yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modüllerini oluşturmak için Visual Basic Derleyicisi çağırır...  

 [Uyarı görevi](../msbuild/warning-task.md)  
 Günlükleri bir derleme sırasında bir uyarı değerlendirilen bir koşullu ifadeye göre.  

 [WriteCodeFragment görevi](../msbuild/writecodefragment-task.md)  
 Belirtilen oluşturulan kod parçasını kullanarak geçici bir kod dosyası oluşturur. Dosya silinmez.  

 [WriteLinesToFile görevi](../msbuild/writelinestofile-task.md)  
 Belirtilen öğelerin belirtilen bir metin dosyasına yazar.  

 [XmlPeek görevi](../msbuild/xmlpeek-task.md)  
 Bir XML dosyasından XPath sorgusu tarafından belirtilen değerleri döndürür.  

 [XmlPoke görevi](../msbuild/xmlpoke-task.md)  
 Bir XML dosyasına bir XPath sorgusu tarafından belirtilen değerleri ayarlar.  

 [XslTransformation görevi](../msbuild/xsltransformation-task.md)  
 Kullanarak bir XML girişi dönüştürür bir *Genişletilebilir Stil Sayfası Dili Dönüşümü* (XSLT) veya XSLT ve çıktıları çıktı cihazına veya bir dosya için derlenmiş.  

  [ZipDirectory görevi](../msbuild/zipdirectory-task.md)  
 Oluşturur bir *.zip* bir dizinin içeriklerini arşivden.

## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev yazma](../msbuild/task-writing.md)   
 [Görevler](../msbuild/msbuild-tasks.md)