---
title: MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
caps.latest.revision: 62
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a2ca3a14c1e4e35da4e8cddfdecb0346740286a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837769"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] Uygulamaları oluşturmaya yönelik bir platformdur. MSBuild olarak da bilinen olduğundan, bu altyapı, yapı platformunu nasıl işler ve yazılım yapıları denetleyen bir proje dosyası için bir XML Şeması sağlar. Visual Studio MSBuild kullanır, ancak Visual Studio'ya bağımlı değildir. MSBuild.exe, proje veya çözüm dosyasında çağırarak, düzenlemek ve Visual Studio'nun yüklü olmayan ortamlarda ürünler oluşturun.  
  
 Visual Studio, yönetilen projeleri yüklemek ve derlemek için MSBuild kullanır. Proje dosyaları (.csproj, .vbproj, vcxproj ve diğerleri) Visual Studio IDE'yi kullanarak proje oluşturduğunuzda yürüten MSBuild XML kodunu içerir. Visual Studio projeleri gerekli tüm ayarları içeri aktarmak ve işlemleri tipik geliştirme işleri için derleme, ancak genişletebilir ve bunları Visual Studio içinde veya bir XML düzenleyicisini kullanarak değiştirin.  
  
 C++ için MSBuild hakkında bilgi için bkz: [MSBuild (Visual C++)](http://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Visual Studio IDE'si yerine MSBuild komut satırını kullanarak derlemeler çalıştırdığınızda, aşağıdaki örnekler gösterilmektedir.  
  
- Visual Studio yüklü değil.  
  
- MSBuild'in 64-bit sürümünü kullanmak istiyorsunuz. MSBuild'in bu sürümü genellikle gereksizdir, ancak MSBuild daha fazla belleğe erişmesini sağlar.  
  
- Bir derlemeyi birden fazla işlemde çalıştırmak istiyorsunuz. Bununla birlikte, C++ ve C# ' deki projelerde aynı sonucu elde etmek için IDE kullanabilirsiniz.  
  
- Derleme sistemini değiştirmek istiyorsunuz. Örneğin, aşağıdaki eylemleri etkinleştirmek isteyebilirsiniz:  
  
  -   Derleyiciye ulaşmadan önce dosyaları ön işlemden geçirin.  
  
  -   Yapı çıktılarını farklı bir konuma kopyalayın.  
  
  -   Yapı çıktılarından sıkıştırılmış dosyalar oluşturun.  
  
  -   Bir sonradan işleme adımı yapın. Örneğin, bir derleme farklı bir sürüm ile damgalamak isteyebilirsiniz.  
  
  Visual Studio IDE'de kod yazabilir buna karşın derlemeleri Msbuild'i kullanarak Çalıştır. Başka bir alternatif olarak IDE içindeki kodu geliştirme bilgisayarında oluşturabilirsiniz, ancak birden çok geliştiriciden tümleştirilen kodu oluşturmak için MSBuild komut satırını kullanın.  
  
> [!NOTE]
>  Otomatik olarak derlemek, test ve uygulamanızı dağıtmak için Team Foundation Build'ı kullanabilirsiniz. Geliştiriciler kodu (örneğin, bir sürekli tümleştirme stratejisinin parçası olarak) iade ettiğinde veya uygun bir zamanlama (örneğin, bir gecelik yapı doğrulama testi derlemesinde) otomatik olarak yapı sistemi kullanabilirsiniz. Team Foundation derlemesi kodunuzu Msbuild'i kullanarak derler. Daha fazla bilgi için [uygulamayı derleyin](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
 Bu konu, MSBuild genel bir bakış sağlar. Giriş niteliğindeki bir eğitim için bkz. [izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).  
  
 **Bu konudaki**  
  
-   [Bir komut isteminde MSBuild kullanma](#BKMK_CommandPrompt)  
  
-   [Proje dosyası](#BKMK_ProjectFile)  
  
    -   [Özellikler](#BKMK_Properties)  
  
    -   [Öğeler](#BKMK_Items)  
  
    -   [Görevler](#BKMK_Tasks)  
  
    -   [Hedefler](#BKMK_Targets)  
  
-   [Derleme günlükleri](#BKMK_BuildLogs)  
  
-   [Visual Studio'da MSBuild kullanma](#BKMK_VisualStudio)  
  
-   [Çoklu Sürüm Desteği](#BKMK_Multitargeting)  
  
##  <a name="BKMK_CommandPrompt"></a> Bir komut isteminde MSBuild kullanma  
 Çalıştırılacak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] komut isteminde, bir proje dosyası MSBuild.exe için uygun komut satırı seçenekleriyle birlikte geçirin. Komut satırı seçenekleri özellikleri ayarlamak, belirli hedefleri yürütmenizi ve yapı işlemini denetleyen diğer seçenekleri belirlemenizi sağlar. Örneğin, dosyayı oluşturmak için aşağıdaki komut satırı sözdizimini kullanırsınız `MyProj.proj` ile `Configuration` özelliğini `Debug`.  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] komut satırı seçenekleri görmek [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
>  Bir proje indirmeden önce kodun güvenilirliğini belirleyin.  
  
##  <a name="BKMK_ProjectFile"></a> Proje dosyası  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kolay anlaşılan ve genişletilebilen XML tabanlı proje dosyası biçimi kullanır. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyası biçimi, geliştiricilerin derlenecek öğeleri sağlar ve ayrıca nasıl bunlar farklı işletim sistemleri ve yapılandırmalar için oluşturulacak. Ayrıca, proje dosyası biçimi ayrı dosyalara faktörlenebilen ve böylece yapılar ürün içindeki farklı projelerde tutarlı bir şekilde gerçekleştirilebilir geliştiriciler Yazar yeniden kullanılabilir yapı kuralları yazmasını sağlar.  
  
 Aşağıdaki bölümlerde temel öğelerinden bazıları açıklanmaktadır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyası biçimi. Temel Proje dosyasının nasıl oluşturulacağı hakkında bir öğretici için bkz. [izlenecek yol: sıfırdan bir MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
###  <a name="BKMK_Properties"></a> Özellikleri  
 Özellikler, yapıları yapılandırmak için kullanılabilen anahtar/değer çiftleri temsil eder. Özellikler, özelliğin adı alt öğesi olarak içeren bir öğe oluşturularak bildirilir bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesi. Örneğin, aşağıdaki kod adında bir özellik oluşturur `BuildDir` değerine sahip `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Yerleştirerek bir özellik koşullu olarak tanımlayabilirsiniz bir `Condition` öğesindeki özniteliği. Koşullu öğelerin içeriği, koşul olarak değerlendirilmedikçe yoksayılır `true`. Aşağıdaki örnekte, `Configuration` öğesi henüz tanımlanmamışsa tanımlanır.  
  
```  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 Özellikleri başvurulabilir proje dosyası boyunca sözdizimi $ kullanarak (*PropertyName*). Kullanarak önceki örneklerde özellikleri gibi başvurabilirsiniz `$(BuildDir)` ve `$(Configuration)`.  
  
 Özellikleri hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](msbuild-properties1.md).  
  
###  <a name="BKMK_Items"></a> Öğeleri  
 Öğeler Yapı sistemine girdi ve genelde dosyaları temsil ederler. Öğeleri, kullanıcı tanımlı öğe adları öğe türlerine içinde gruplandırılır. Bu öğe türleri, ayrı ayrı öğeleri derleme işleminin adımları gerçekleştirmek için kullanacağınız görevler için parametre olarak kullanılabilir.  
  
 Öğe, öğe türünün adı bir alt öğesi olarak içeren bir öğe oluşturularak proje dosyasında bildirilir bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesi. Örneğin, aşağıdaki kodu adlı bir öğe türü oluşturur `Compile`, iki dosya içerir.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Öğe türleri başvurulabilir proje dosyası boyunca sözdizimi kullanarak @(*Itemtype*). Örneğin örnekteki öğe türü kullanarak başvurulabilir `@(Compile)`.  
  
 Msbuild'de öğe ve öznitelik adları büyük/küçük harf duyarlıdır. Ancak, özelliği, öğe ve meta veri adları değildir. Aşağıdaki örnek, öğe türü oluşturur. `Compile`, `comPile`, veya harf çeşitlemesini ve öğe türüne "one.cs;two.cs" değerini verir.  
  
```  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Öğeler joker karakterler kullanılarak bildirilebilir ve daha gelişmiş yapı senaryoları için ek meta veriler içerebilir. Öğeler hakkında daha fazla bilgi için bkz. [öğeleri](../msbuild/msbuild-items.md).  
  
###  <a name="BKMK_Tasks"></a> Görevleri  
 Görevleridir yürütülebilir koddur, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projeleri derleme işlemlerini gerçekleştirmek için kullanın. Örneğin, bir görev giriş dosyalarını derleyebilir ya da bir harici araç çalıştırabilir. Görevler tekrar kullanılabilir ve bunlar farklı projelerde farklı geliştiriciler tarafından paylaşılabilir.  
  
 Bir görevin yürütülme mantığı yönetilen kodda yazılır ve eşlenen [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kullanarak [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi. Uygulayan yönetilen bir tür geliştirerek kendi görevinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ITask> arabirimi. Görevlerin nasıl yazılacağı hakkında daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] gereksinimlerinize uydurmak için değiştirebileceğiniz değiştirebileceğiniz Orta görevleri içerir.  Örnekler [kopyalama](../msbuild/copy-task.md), dosyaları kopyalayan [MakeDir](../msbuild/makedir-task.md), dizinler oluşturan ve [Csc](../msbuild/csc-task.md), Visual C# kaynak kodu dosyaları derler. Kullanım bilgileri ile birlikte kullanılabilir görevlerin bir listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
 Bir görev yürütüldü bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] alt öğesi olarak görev adına sahip bir öğe oluşturularak proje dosyası bir [hedef](../msbuild/target-element-msbuild.md) öğesi. Görevler genellikle öğenin öznitelikleri geçirilen parametreleri kabul eder. Her ikisi de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] özellikleri ve öğeleri parametreler olarak kullanılabilir. Örneğin, aşağıdaki çağrıları kod [MakeDir](../msbuild/makedir-task.md) değerini geçirir ve görev `BuildDir` önceki örnekte bildirilen özellik.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Görevler hakkında daha fazla bilgi için bkz. [görevleri](../msbuild/msbuild-tasks.md).  
  
###  <a name="BKMK_Targets"></a> Hedefleri  
 Hedefler görevleri belirli bir sıraya göre gruplandırabilir ve proje dosyasının bölümlerini derleme işlemine giriş noktaları olarak kullanıma sunar. Hedefleri, genellikle okunabilirliğini artırmak ve genişletmeye izin vermek için mantıksal bölümler halinde gruplandırılır. Yapı adımlarını hedeflere parçalamak, kodun o bölümünü her hedefe kopyalamadan yapı işleminin bir parçasını diğer hedeflerden çağrı olanak tanır. Örneğin, yapı işlemine birden çok giriş noktası yapıya başvurular gerekiyorsa, başvuruları oluşturan bir hedef oluşturabilir ve ardından bu hedef, gerekli olan her giriş noktasından çalıştırabilirsiniz.  
  
 Kullanarak hedefler proje dosyasında bildirilir [hedef](../msbuild/target-element-msbuild.md) öğesi. Örneğin, aşağıdaki kod adında bir hedef oluşturur `Compile`, sonra çağıran [Csc](../msbuild/csc-task.md) önceki örnekte bildirilen öğe listesine sahip görev.  
  
```  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Daha gelişmiş senaryolarda, hedefler birbirleri arasındaki ilişkileri tanımlamak ve böylece yapı işleminin tüm bölümleri hedefin güncel olması durumunda atlanabilir bağımlılık analizleri gerçekleştirmek için kullanılabilir. Hedefleri hakkında daha fazla bilgi için bkz. [hedefleri](../msbuild/msbuild-targets.md).  
  
##  <a name="BKMK_BuildLogs"></a> Derleme günlükleri  
 Derleme hatalarını, uyarılarını ve iletileri konsolda veya başka bir çıktı cihazına oturum açabilir. Daha fazla bilgi için [derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md) ve [Msbuild'de günlük kaydı](../msbuild/logging-in-msbuild.md).  
  
##  <a name="BKMK_VisualStudio"></a> Visual Studio'da MSBuild kullanma  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanan [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] yönetilen projeler hakkında derleme bilgileri depolamak için proje dosyası biçimi. Proje, eklenen veya değiştirilen kullanarak ayarları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] arabirimi yansıtılır. * oluşturulan proj dosyasında her proje için. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] barındırılan bir örneğini kullanan [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] yönetilen projeleri derlemek için. Bir yönetilen projenin derlenmesi, yani [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya bir komut isteminde (bile [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklü değilse), ve sonuçları aynı olur.  
  
 Visual Studio'da MSBuild kullanma hakkında bir öğretici için bkz. [izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).  
  
##  <a name="BKMK_Multitargeting"></a> Çoklu sürüm desteği  
 Visual Studio kullanarak, .NET Framework'ün çeşitli sürümlerinden herhangi biri üzerinde çalışacak bir uygulamayı derleyebilirsiniz. Örneğin, bir 32 bit platformda .NET Framework 2.0 üzerinde çalışacak bir uygulamayı derleyebilir ve aynı uygulamayı 64 bitlik bir platformda .NET Framework 4.5 çalışacak şekilde derleyebilirsiniz. Birden fazla framework derleme olanağı çok hedefli derleme denir.  
  
 Çoklu sürüm desteği avantajlarından bazıları şunlardır:  
  
- .NET Framework'ün önceki sürümlerinde Örneğin, 2.0, 3.0 ve 3.5 sürümleri hedefleyen uygulamalar geliştirebilirsiniz.  
  
- .NET Framework, örneğin, Silverlight başka çerçeveleri hedefleyebilirsiniz.  
  
- Platformlarını hedefleyebilen bir *framework profili*, hangi hedef framework'ün önceden tanımlanmış bir alt kümesidir.  
  
- Geçerli .NET Framework sürümü için bir hizmet paketi yayımlandığında bunu hedefleyebilirsiniz.  
  
- Çoklu hedefleme, uygulamanın yalnızca hedef framework ve platformda mevcut olan işlevselliği kullandığı garanti eder.  
  
  Daha fazla bilgi için [çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek Yol: Sıfırdan MSBuild Proje Dosyası Oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Basit bir proje dosyasının aşamalı olarak, yalnızca bir metin düzenleyicisi kullanarak oluşturmanız gösterilmektedir.|  
|[İzlenecek Yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md)|MSBuild'in yapı bloklarını tanıtır ve MSBuild projelerinin Visual Studio IDE kapatılmadan hata ayıklama yazma ve düzenleme işlemi gösterilmektedir.|  
|[MSBuild Kavramları](../msbuild/msbuild-concepts.md)|MSBuild'in dört yapı bloğunu sunar: özellikler, öğeleri, hedefler ve görevler.|  
|[Öğeler](../msbuild/msbuild-items.md)|Ardındaki genel kavramları açıklar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dosya biçimi ve nasıl parçaları bir araya getireceğinizi.|  
|[MSBuild Özellikleri](msbuild-properties1.md)|Özellikler ve özellik koleksiyonları tanıtır. Özellikler, yapıları yapılandırmak için kullanılan anahtar/değer çiftleri olur.|  
|[Hedefler](../msbuild/msbuild-targets.md)|Belirli bir sırada görevleri gruplandırın ve komut satırında çağrılacak yapı işlemi bölümlerinin etkinleştirme açıklanmaktadır.|  
|[Görevler](../msbuild/msbuild-tasks.md)|Tarafından kullanılan yürütülebilir kod biriminin nasıl oluşturulacağını gösterir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] CAN atomik yapı işlemleri gerçekleştirmek için.|  
|[Koşullar](../msbuild/msbuild-conditions.md)|Nasıl kullanılacağı ele alınmaktadır `Condition` özniteliğinin bir MSBuild öğesinde.|  
|[Gelişmiş Kavramlar](../msbuild/msbuild-advanced-concepts.md)|Toplu işleme, dönüşümler, çoklu hedefleme ve diğer gelişmiş teknikleri gerçekleştirmek sunar.|  
|[MSBuild'de Günlük Kaydı](../msbuild/logging-in-msbuild.md)|Yapı olaylarının, iletilerin ve hataların günlüğünün nasıl açıklar.|  
|[Ek Kaynaklar](../msbuild/additional-msbuild-resources.md)|MSBuild hakkında daha fazla bilgi için topluluk ve destek kaynaklarını listeler.|  
  
## <a name="reference"></a>Başvuru  
 [MSBuild Başvurusu](../msbuild/msbuild-reference.md)  
 Başvuru bilgilerini içeren konulara bağlantılar.  
  
 Sözlük  
 Ortak MSBuild terimlerini tanımlar.





