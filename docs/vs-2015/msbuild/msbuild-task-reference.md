---
title: MSBuild görev başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6f1767ce1c572e1e3d8eacae8ba3a60f3593476
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193999"
---
# <a name="msbuild-task-reference"></a>MSBuild Görev Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevleri aşağıdaki listede bulunan [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Zaman [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] yüklenen, ek görevler oluşturmak için kullanılan olan [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projeleri. Daha fazla bilgi için [Visual C++ görevleri](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Bu bölümdeki konular, listelenen parametrelerin yanı sıra, her görev, ayrıca aşağıdaki parametrelere sahiptir:  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı `String` parametresi.<br /><br /> A `Boolean` ifade eden [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] altyapısı bu görevi yürüten olup olmadığını belirlemek için kullanır. Tarafından desteklenen koşullar hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], bkz: [koşullar](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, sonraki görevlerinde [hedef](../msbuild/target-element-msbuild.md) öğesi ile derleme devam yürütülecek ve görevin tüm hataları uyarı olarak kabul edilir.<br />-   **ErrorAndContinue**. Bir görev başarısız olduğunda, sonraki görevlerinde `Target` öğesi ile derleme devam yürütmek ve tüm hataları görev hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, listesindeki kalan görevlere `Target` olmayan öğe ve derleme yürütülür ve tüm `Target` öğesi ve yapı başarısız olduğu değerlendirilir.<br /><br /> .NET Framework 4.5 yalnızca desteklenen önce sürümleri `true` ve `false` değerleri.<br /><br /> Daha fazla bilgi için [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Task Temel Sınıfı](../msbuild/task-base-class.md)  
 Öğesinden türetilen görevleri birkaç parametre ekler <xref:Microsoft.Build.Utilities.Task> sınıfı.  
  
 [TaskExtension Temel Sınıfı](../msbuild/taskextension-base-class.md)  
 Öğesinden türetilen görevleri birkaç parametre ekler <xref:Microsoft.Build.Tasks.TaskExtension> sınıfı.  
  
 [ToolTaskExtension Temel Sınıfı](../msbuild/tooltaskextension-base-class.md)  
 Öğesinden türetilen görevleri birkaç parametre ekler <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfı.  
  
 [AL (Derleme Bağlayıcı) Görevi](../msbuild/al-assembly-linker-task.md)  
 Bir modül olan bir veya daha fazla veya kaynak dosyalar bildiriminden bir derleme oluşturur.  
  
 [AspNetCompiler Görevi](../msbuild/aspnetcompiler-task.md)  
 Aspnet_compiler.exe, ASP.NET uygulamalarının önceden derlemek için bir yardımcı program sarmalar.  
  
 [AssignCulture Görevi](../msbuild/assignculture-task.md)  
 Kültür tanımlayıcıları öğesine atar.  
  
 [AssignProjectConfiguration Görevi](../msbuild/assignprojectconfiguration-task.md)  
 Yapılandırma dizeleri listesini kabul eder ve bunları belirtilen projelere atar.  
  
 [AssignTargetPath Görevi](../msbuild/assigntargetpath-task.md)  
 Dosyaların bir listesini kabul eder ve ekler `<TargetPath>` zaten belirtilmezse, öznitelikleri.  
  
 [CallTarget Görevi](../msbuild/calltarget-task.md)  
 Bir hedef proje dosyasındaki çağırır.  
  
 [CombinePath Görevi](../msbuild/combinepath-task.md)  
 Belirtilen yolu tek yola birleştirir.  
  
 [ConvertToAbsolutePath Görevi](../msbuild/converttoabsolutepath-task.md)  
 Bir göreli yol veya başvuru bir mutlak yola dönüştürür.  
  
 [Copy Görevi](../msbuild/copy-task.md)  
 Dosyaları yeni bir konuma kopyalar.  
  
 [CreateCSharpManifestResourceName Görevi](../msbuild/createcsharpmanifestresourcename-task.md)  
 Oluşturur bir [!INCLUDE[csprcs](../includes/csprcs-md.md)]-belirtilen .resx dosya adı veya diğer kaynak bildirim adı stili.  
  
 [CreateItem Görevi](../msbuild/createitem-task.md)  
 Girdi öğelerinin öğeleri bir listeden diğerine kopyalanmasına izin verme, öğe koleksiyonlarını doldurur.  
  
 [CreateProperty Görevi](../msbuild/createproperty-task.md)  
 Bir özellik veya dize diğerine kopyalanması için değerler sağlayan giriş değerleri özelliklerinden doldurur.  
  
 [CreateVisualBasicManifestResourceName Görevi](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Oluşturur bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-belirtilen .resx dosya adı veya diğer kaynak bildirim adı stili.  
  
 [Csc Görevi](../msbuild/csc-task.md)  
 Yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modüllerini oluşturmak için Visual C# derleyicisini çağırır.  
  
 [Delete Görevi](../msbuild/delete-task.md)  
 Belirtilen dosyaları siler.  
  
 [Error Görevi](../msbuild/error-task.md)  
 Bir derleme durdurur ve değerlendirilen bir koşullu ifadeye göre bir hatayı günlüğe kaydeder.  
  
 [Exec Görevi](../msbuild/exec-task.md)  
 Belirtilen bağımsız değişkenlerle belirtilen program veya komut çalıştırır.  
  
 [FindAppConfigFile Görevi](../msbuild/findappconfigfile-task.md)  
 Sağlanan listelerinde app.config dosyasına bulur  
  
 [FindInList Görevi](../msbuild/findinlist-task.md)  
 Eşleşen öğebelirtimi belirtilen bir listede bir öğe bulur.  
  
 [FindUnderPath Görevi](../msbuild/findunderpath-task.md)  
 Belirtilen öğe koleksiyonunda öğelerin belirtilen klasörde ve alt klasörlerindeki tüm mevcut belirler.  
  
 [FormatUrl Görevi](../msbuild/formaturl-task.md)  
 Bir URL doğru bir URL biçimine dönüştürür.  
  
 [FormatVersion Görevi](../msbuild/formatversion-task.md)  
 Düzeltme numarası için sürüm numarası ekler.  
  
 [GenerateApplicationManifest Görevi](../msbuild/generateapplicationmanifest-task.md)  
 Oluşturur bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi ya da yerel bir bildirim.  
  
 [GenerateBootstrapper Görevi](../msbuild/generatebootstrapper-task.md)  
 Algılama, indirmek ve bir uygulama ve önkoşulları yüklemek için otomatik bir yol sağlar.  
  
 [GenerateDeploymentManifest Görevi](../msbuild/generatedeploymentmanifest-task.md)  
 Oluşturur bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimi.  
  
 [GenerateResource Görevi](../msbuild/generateresource-task.md)  
 .Txt ve .resx dosyalarını ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürür.  
  
 [GenerateTrustInfo Görevi](../msbuild/generatetrustinfo-task.md)  
 Uygulama güvenini taban bildirimini ve gelen oluşturur `TargetZone` ve `ExcludedPermissions` parametreleri.  
  
 [GetAssemblyIdentity Görevi](../msbuild/getassemblyidentity-task.md)  
 Belirtilen dosyalardan derleme kimlikleri alır ve kimlik bilgilerini çıkarır.  
  
 [GetFrameworkPath Görevi](../msbuild/getframeworkpath-task.md)  
 Yolunu alır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] derlemeler.  
  
 [GetFrameworkSdkPath Görevi](../msbuild/getframeworksdkpath-task.md)  
 Yolunu alır [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
 [GetReferenceAssemblyPaths Görevi](../msbuild/getreferenceassemblypaths-task.md)  
 Başvuru bütünleştirilmiş kodu yolları çeşitli çerçevesini döndürür.  
  
 [LC Görevi](../msbuild/lc-task.md)  
 Bir .licx dosyasından .license dosyası oluşturur.  
  
 [MakeDir Görevi](../msbuild/makedir-task.md)  
 Dizin oluşturur ve gerekirse, tüm üst dizinleri.  
  
 [Message Görevi](../msbuild/message-task.md)  
 Derleme sırasında bir ileti kaydeder.  
  
 [Move Görevi](../msbuild/move-task.md)  
 Dosyalarını yeni konuma taşır.  
  
 [MSBuild Görevi](../msbuild/msbuild-task.md)  
 Yapılar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] başka projelerden [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje.  
  
 [ReadLinesFromFile Görevi](../msbuild/readlinesfromfile-task.md)  
 Öğe listesini bir metin dosyasından okur.  
  
 [RegisterAssembly Görevi](../msbuild/registerassembly-task.md)  
 Belirtilen derleme içindeki meta veriyi okur ve kayıt defterine gerekli girişleri ekler.  
  
 [RemoveDir Görevi](../msbuild/removedir-task.md)  
 Belirtilen dizinlerin ve tüm alt dizinleri ve dosyaları kaldırır.  
  
 [RemoveDuplicates Görevi](../msbuild/removeduplicates-task.md)  
 Yinelenen öğeleri belirtilen öğeyi koleksiyondan kaldırır.  
  
 [RequiresFramework35SP1Assembly Görevi](../msbuild/requiresframework35sp1assembly-task.md)  
 Uygulama .NET Framework 3.5 SP1 isteyip istemediğini belirler.  
  
 ResGen görevi  
 Kullanımdan kalktı. Kullanım [GenerateResource görevi](../msbuild/generateresource-task.md) .txt ve .resx dosyaları için ve ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürmek için görev.  
  
 [ResolveAssemblyReference Görevi](../msbuild/resolveassemblyreference-task.md)  
 Belirtilen derlemelerini bağımlı derlemelerin belirler.  
  
 [ResolveComReference Görevi](../msbuild/resolvecomreference-task.md)  
 Bir veya daha fazla tür kitaplığı adları veya .tlb dosyaları listesini alır ve bu tür kitaplıklarını disk üzerindeki konumlara giderir.  
  
 [ResolveKeySource Görevi](../msbuild/resolvekeysource-task.md)  
 Tanımlayıcı ad anahtar kaynağını belirler  
  
 [ResolveManifestFiles Görevi](../msbuild/resolvemanifestfiles-task.md)  
 Yapı işleminde aşağıdaki öğeleri için bildirim üretme dosyaları giderir: öğe, bağımlılıkları, Uyduları, içerik, hata ayıklama sembolleri ve belgeleri yerleşik.  
  
 [ResolveNativeReference Görevi](../msbuild/resolvenativereference-task.md)  
 Yerel başvurular çözümleniyor.  
  
 [ResolveNonMSBuildProjectOutput Görevi](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 MSBuild dışındaki proje başvuruları için çıkış dosyalarının belirler.  
  
 [SGen Görevi](../msbuild/sgen-task.md)  
 Bir XML serileştirme derleme türleri için belirtilen derlemesinde oluşturur.  
  
 [SignFile Görevi](../msbuild/signfile-task.md)  
 Belirtilen dosyayı belirtilen sertifikayı kullanarak imzalar.  
  
 [Touch Görevi](../msbuild/touch-task.md)  
 Dosya erişim ve değişiklik saatlerini ayarlar.  
  
 [UnregisterAssembly Görevi](../msbuild/unregisterassembly-task.md)  
 Belirtilen derlemeleri COM birlikte çalışma amacıyla kaydını siler.  
  
 [UpdateManifest Görevi](../msbuild/updatemanifest-task.md)  
 Bir bildirimdeki seçili özelliklerini güncelleştirir ve Çekildi.  
  
 [Vbc Görevi](../msbuild/vbc-task.md)  
 Yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modüllerini oluşturmak için Visual Basic Derleyicisi çağırır...  
  
 [Warning Görevi](../msbuild/warning-task.md)  
 Günlükleri bir derleme sırasında bir uyarı değerlendirilen bir koşullu ifadeye göre.  
  
 [WriteCodeFragment Görevi](../msbuild/writecodefragment-task.md)  
 Belirtilen oluşturulan kod parçasını kullanarak geçici bir kod dosyası oluşturur. Dosya silinmez.  
  
 [WriteLinesToFile Görevi](../msbuild/writelinestofile-task.md)  
 Belirtilen öğelerin belirtilen bir metin dosyasına yazar.  
  
 [XmlPeek Görevi](../msbuild/xmlpeek-task.md)  
 Bir XML dosyasından XPath sorgusu tarafından belirtilen değerleri döndürür.  
  
 [XmlPoke Görevi](../msbuild/xmlpoke-task.md)  
 Bir XML dosyasına bir XPath sorgusu tarafından belirtilen değerleri ayarlar.  
  
 [XslTransformation Görevi](../msbuild/xsltransformation-task.md)  
 Kullanarak bir XML girişi dönüştürür bir *Genişletilebilir Stil Sayfası Dili Dönüşümü* (XSLT) veya XSLT ve çıktıları çıktı cihazına veya bir dosya için derlenmiş.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev yazma](../msbuild/task-writing.md)   
 [Görevler](../msbuild/msbuild-tasks.md)



