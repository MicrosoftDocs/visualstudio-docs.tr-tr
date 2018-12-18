---
title: Yaygın MSBuild proje öğeleri | Microsoft Docs
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
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d4975390802c8a04459750be5e5405bd17c3a68
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238413"
---
# <a name="common-msbuild-project-items"></a>Yaygın MSBuild Proje Öğeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
İçinde [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], adlandırılmış bir veya daha fazla dosya başvurusu bir öğedir. Meta veri dosya adları, yollar ve sürüm numaraları gibi öğeleri içerir. Tüm proje türlerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çeşitli öğeleri ortaktır. Bu öğeler, dosya Microsoft.Build.commontypes.xsd'de tanımlanmıştır.  
  
## <a name="common-items"></a>Ortak öğeler  
 Ortak proje öğeleri listesi verilmiştir.  
  
### <a name="reference"></a>Başvuru  
 Projesinde bir derleme (yönetilen) başvuruyu temsil eder.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|HintPath|İsteğe bağlı dize. Derlemenin göreli veya mutlak yolu.|  
|Ad|İsteğe bağlı dize. Örneğin, "System.Windows.Forms." derlemenin görünen adı|  
|FusionName|İsteğe bağlı dize. Öğe için basit veya güçlü Füzyon adı belirtir.<br /><br /> Bu öznitelik mevcut olduğunda, derleme dosyasını Füzyon adı almak için açık olması gerekmez çünkü zaman kazandırabilir.|  
|SpecificVersion|İsteğe bağlı boolean. Sadece Füzyon adındaki sürümünde başvuruda bulunup bulunmadığını belirtir.|  
|Diğer adlar|İsteğe bağlı dize. Başvuru için diğer adlar.|  
|Özel|İsteğe bağlı boolean. Başvurunun çıkış klasörüne kopyalanıp kopyalanmayacağını belirtir. Bu özniteliği ile eşleşen **Yereli Kopyala** Visual Studio IDE içinde olan başvuru özelliği.|  
  
### <a name="comreference"></a>COMReference  
 Temsil eder (yönetilmeyen) COM bileşeni projede başvuru.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|Ad|İsteğe bağlı dize. Bileşenin görünen adı.|  
|Guid|İsteğe bağlı dize. Bir GUID biçiminde bileşeni için {12345678-1234-1234-1234-1234567891234}.|  
|VersionMajor|İsteğe bağlı dize. Bileşenin sürüm numarasının ana bölümü. Örneğin, "5" tam sürüm numarası "5.46." ise|  
|VersionMinor|İsteğe bağlı dize. Bileşenin sürüm numarasının ikincil bölümü. Örneğin, "46" tam sürüm numarası "5.46." ise|  
|LCID|İsteğe bağlı dize. LocaleID bileşeni için.|  
|WrapperTool|İsteğe bağlı dize. Bileşen, örneğin, "tlbimp." kullanılan sarmalayıcı aracı adı|  
|Yalıtılmış|İsteğe bağlı boolean. Bileşen reg ücretsiz bir bileşen olup olmadığını belirtir.|  
  
### <a name="comfilereference"></a>COMFileReference  
 Akış ResolvedComreference hedef tür kitaplıklarını listesini temsil eder.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|WrapperTool|İsteğe bağlı dize. Bileşen, örneğin, "tlbimp." kullanılan sarmalayıcı aracı adı|  
  
### <a name="nativereference"></a>NativeReference  
 Yerel bir bildirim dosyası veya böyle bir dosya başvurusu temsil eder.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|Ad|Zorunlu dize. Bildirim dosyasının temel adı.|  
|HintPath|Zorunlu dize. Bildirim dosyasının göreli yolu.|  
  
### <a name="projectreference"></a>ProjectReference  
 Başka bir projeye başvuruyu temsil eder.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|Ad|İsteğe bağlı dize. Başvurunun görünen adı.|  
|Proje|İsteğe bağlı dize. Bir GUID biçiminde başvuru {12345678-1234-1234-1234-1234567891234}.|  
|Paket|İsteğe bağlı dize. Başvurulan proje dosyasının yolu.|  
  
### <a name="compile"></a>Derleme  
 Derleyici için kaynak dosyaları temsil eder.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Bu dosyayı doğru şekilde derlenmesi için bağımlı dosyasını belirtir.|  
|AutoGen|İsteğe bağlı boolean. Dosya için proje tarafından oluşturulup oluşturulmadığını gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE).|  
|Bağlantı|İsteğe bağlı dize. Dosya fiziksel olarak proje dosyasının etkisi dışında bulunduğunda görüntülenecek notational yolu.|  
|Görünür|İsteğe bağlı boolean. Dosyada görüntülenip görüntülenmeyeceğini gösterir **Çözüm Gezgini** içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyayı çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1.  hiçbir zaman<br />2.  Her zaman<br />3.  PreserveNewest|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Üretilen derleme içine gömülü olması için kaynaklar temsil eder.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Bu dosyayı doğru şekilde derlenmesi için bağımlı dosyasını belirtir|  
|Oluşturucu|Zorunlu dize. Bu öğe üzerinde çalıştırılmış herhangi bir dosya üreticisinin adı.|  
|LastGenOutput|Zorunlu dize. Bu öğe üzerinde çalışan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı.|  
|CustomToolNamespace|Zorunlu dize. Hangi herhangi bir dosyada bu öğe üzerinde çalışan bir Oluşturucu kod üretmesi gereken ad alanı.|  
|Bağlantı|İsteğe bağlı dize. Dosya fiziksel olarak proje etki dışında yer alıyorsa notational yolu görüntülenir.|  
|Görünür|İsteğe bağlı boolean. Dosyada görüntülenip görüntülenmeyeceğini gösterir **Çözüm Gezgini** içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyayı çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1.  hiçbir zaman<br />2.  Her zaman<br />3.  PreserveNewest|  
|LogicalName|Zorunlu dize. Katıştırılmış kaynağın mantıksal adı.|  
  
### <a name="content"></a>İçerik  
 Projeye derlenmemiş ancak katıştırılmış veya olabilir, birlikte yayımlanan dosyaları gösterir.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Bu dosyayı doğru şekilde derlenmesi için bağımlı dosyasını belirtir.|  
|Oluşturucu|Zorunlu dize. Bu öğe üzerinde çalışan herhangi bir dosya üreticisinin adı.|  
|LastGenOutput|Zorunlu dize. Bu öğe üzerinde çalıştırılmış herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı.|  
|CustomToolNamespace|Zorunlu dize. Hangi herhangi bir dosyada bu öğe üzerinde çalışan bir Oluşturucu kod üretmesi gereken ad alanı.|  
|Bağlantı|İsteğe bağlı boolean. Dosyada görüntülenip görüntülenmeyeceğini gösterir **Çözüm Gezgini** içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|PublishState|Zorunlu dize. İçerik Yayımlama durumu ya da:<br /><br /> -Varsayılan<br />-Dahil<br />-Dışlanan<br />-Veri dosyası<br />-Önkoşulu|  
|IsAssembly|İsteğe bağlı boolean. Dosyanın derleme olup olmadığını belirtir.|  
|Görünür|İsteğe bağlı boolean. Dosyada görüntülenip görüntülenmeyeceğini gösterir **Çözüm Gezgini** içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyayı çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1.  hiçbir zaman<br />2.  Her zaman<br />3.  PreserveNewest|  
  
### <a name="none"></a>Yok.  
 Derleme işleminde hiçbir rolü olması gereken dosyaları temsil eder.  
  
|Öğe adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Bu dosyayı doğru şekilde derlenmesi için bağımlı dosyasını belirtir.|  
|Oluşturucu|Zorunlu dize. Bu öğe üzerinde çalıştırılmış herhangi bir dosya üreticisinin adı.|  
|LastGenOutput|Zorunlu dize. Bu öğe üzerinde çalışan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı.|  
|CustomToolNamespace|Zorunlu dize. Hangi herhangi bir dosyada bu öğe üzerinde çalışan bir Oluşturucu kod üretmesi gereken ad alanı.|  
|Bağlantı|İsteğe bağlı dize. Dosya fiziksel olarak proje etki dışında yer alıyorsa görüntülenecek notational yolu.|  
|Görünür|İsteğe bağlı boolean. Dosyada görüntülenip görüntülenmeyeceğini gösterir **Çözüm Gezgini** içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyayı çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1.  hiçbir zaman<br />2.  Her zaman<br />3.  PreserveNewest|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Yapı için temel uygulama bildirimini temsil eder ve içeren [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım güvenlik bilgileri.  
  
### <a name="codeanalysisimport"></a>CodeAnalysisImport  
 İçeri aktarmak için FxCop projesi temsil eder.  
  
### <a name="import"></a>{1&gt;İçeri Aktar&lt;1}  
 Ad uzayları, tarafından aktarılacaksa derlemeleri temsil [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derleyici.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yaygın MSBuild Proje Özellikleri](../msbuild/common-msbuild-project-properties.md)



