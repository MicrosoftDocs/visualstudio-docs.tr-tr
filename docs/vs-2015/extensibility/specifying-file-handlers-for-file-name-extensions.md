---
title: Dosya adı uzantıları için dosya işleyicileri belirtme | Microsoft Docs
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
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0a4f0547da10a4d519d315000a0f35a19a56287
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726243"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli bir dosya uzantısı olan bir dosya işler uygulamayı belirlemek için çeşitli yollarla vardır. OpenWithList ve OpenWithProgids fiilleri dosya uzantısı için kayıt defteri girdisinin altındaki dosya işleyicileri belirtmek için kullanabileceğiniz iki yöntemdir.  
  
## <a name="openwithlist-verb"></a>OpenWithList fiili  
 Windows Gezgini'nde bir dosyaya sağ tıklayın, gördüğünüz **açık** komutu. Birden fazla ürün uzantı ile ilişkili ise, gördüğünüz bir **birlikte Aç** alt.  
  
 Dosya uzantısı için OpenWithList anahtarı HKEY_CLASSES_ROOT ayarlayarak bir uzantı açmak için farklı uygulamaları kaydedebilir. Bir dosya uzantısı için bu anahtarı altında listelenen uygulamalar altında görünür **önerilen program** başlık olarak **birlikte Aç** iletişim kutusu. Aşağıdaki örnek .vcproj dosya uzantısı'nı açmak için kayıtlı uygulamalar gösterilmektedir.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Uygulamalar belirtilerek HKEY_CLASSES_ROOT\Applications altındaki listeden anahtarlarıdır.  
  
 Bir OpenWithList anahtarı ekleyerek, başka bir uygulama uzantısı sahiplenir olsa bile, uygulamanızın bir dosya uzantısı desteklediğini bildirin. Bu, gelecek bir sürümünde uygulamanızı veya başka bir uygulama olabilir.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Programlama tanımlayıcılarını (ProgID), bir uygulama ya da COM nesnesinin sürümünü tanımlayan ClassID kolay sürümleridir. Her birlikte oluşturulabilir nesne kendi ProgID olması gerekir. Örneğin VisualStudio.DTE.10.0 başlatılırken VisualStudio.DTE.7.1 Visual Studio .NET 2003 başlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bir proje türü veya proje öğe türüne sahip olarak, dosya uzantısı için sürüme özgü ProgID oluşturmanız gerekir. Aynı uygulamanın birden fazla ProgID başlayabilir, bu Progid'ler gereksiz olabilir. Daha fazla bilgi için [dosya adı uzantıları için fiil kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Şu adlandırma kuralına sürümlü dosya Progid'ler diğer satıcılardan kaydı ile yinelemesinden kaçınmak için kullanın:  
  
|Dosya uzantısı|Tutulan program kimliği|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Tutulan Progid'ler değerleri olarak i HKEY_CLASSES_ROOT olarak ekleyerek belirli bir dosya uzantısı açmanız mümkün olan farklı uygulamaları kaydedebilir\\*\<uzantısı >* \OpenWithProgids anahtarı. Bu kayıt defteri anahtarı, dosya uzantısıyla ilişkili alternatif ProgIDs bir listesini içerir. Listelenen Progid'ler ile ilişkili uygulamalar görünür **birlikte Aç**_ürün adı_ alt. Aynı uygulama içinde her ikisi de belirtilirse `OpenWithList` ve `OpenWithProgids` yinelenen anahtarlar, işletim sistemi birleştirir.  
  
> [!NOTE]
>  `OpenWithProgids` Anahtarı yalnızca Windows XP'de desteklenir. Diğer işletim sistemlerinin bu anahtarı yok saymak için dosya işleyicileri için tek bir kayıt kullanmayın. Windows XP'de daha iyi bir kullanıcı deneyimi sağlamak için bu anahtarı kullanırsınız.  
  
 İstenen Progid'ler REG_NONE türünde bir değerler ekleyin. Aşağıdaki kod örneği ProgIDs bir dosya uzantısı için kaydetme sağlar (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Varsayılan dosya işleyicisi dosya uzantısı için varsayılan değer olarak belirtilen program kimliği. Önceki bir sürümü ile birlikte gelen bir dosya uzantısı için ProgID değiştirirseniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya diğer uygulamalar tarafından devralınırsa alınabilmesini ve ardından kaydetmeniz gerekir `OpenWithProgids` dosya Uzantınız için anahtar ve yeni ProgID listesi ile birlikte belirtin desteklediğiniz eski Progid'ler. Örneğin:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Eski ProgID ilişkili fiilleri sahiptir. ardından bu fiilleri altında ayrıca görünür **birlikte Aç** *ürün adı* kısayol menüsünde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosya adı uzantıları hakkında](../extensibility/about-file-name-extensions.md)   
 [Dosya Adı Uzantıları için Fiil Kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)

