---
title: Proje türleri oluşturma | Microsoft Docs
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
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58b31e363d78af7902e6174c9683b7e794031263
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756204"
---
# <a name="creating-project-types"></a>Proje Türleri Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Genişletebileceğiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oluşturarak yeni bir proje türü. Yeni bir proje türü oluşturmak için birkaç kavramları anlamanıza ve birkaç adımı tamamlamanız gerekir. Aşağıdaki konular, proje türleri oluşturma konusunda genel bir bakış sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Proje Türü Tasarım Kararları](../../extensibility/internals/project-type-design-decisions.md)  
 Öğesi, proje dosya kalıcılığına ve yeni bir proje türü oluşturmadan önce yapmanız taahhüt teknisyenin tasarım kararları açıklar.  
  
 [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Kod düzenleme ve derleme, derleme, hata ayıklama ve projenizdeki dağıtmaya olarak programlama görevlerini destekleyen yeni bir proje türü oluşturmak için izlemeniz gereken adımlara genel bir bakış sağlar.  
  
 [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Sağlayın ve yeni bir proje örneklerini oluşturmak için bir proje fabrikası kullanma hakkında bilgi sağlar.  
  
 [Proje Türü Kaydetme](../../extensibility/internals/registering-a-project-type.md)  
 Kayıt betiği for each deyimi girişlerinden içeren varsayılan yolları ve verileri bir tablo sağlayan deyimler kayıt defterinden kod örneği sağlanmıştır.  
  
 [Proje Kalıcılığı](../../extensibility/internals/project-persistence.md)  
 Kullanımı anlatılmaktadır `IPersistFileFormat` hem dosya hem de dosya tabanlı olmayan proje nesnelerini kalıcı hale getirmek için.  
  
 [MSBuild Kullanma](../../extensibility/internals/using-msbuild.md)  
 Proje türüne nasıl kullanabileceğinizi açıklar [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] yapıdan kullanıcıların altyapısının yapı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve komut satırına.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Kod araçları gibi görüntüleme mimarisini açıklar **Nesne Tarayıcısı** ve **sınıf görünümü** penceresi. VSPackage'ı nesne tarama uygulamak için kullanılan yöntemleri ve arabirimleri açıklar.  
  
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Bir proje öğesi açıldığında hangi Düzenleyicisi kullanılabilir saptanırken projeleri play önemi açıklanır ve proje kaynaklarını nasıl yönetilebilir.  
  
 [Windows Installer ile VSPackage Yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Benzersiz kimliğini, VSPackage vermek ve bir Windows yükleyici paketinde, VSPackage DLL'ler ve diğer bilgileri sarmalama gösterir (. MSI dosyası) dağıtım müşterileriniz için.  
  
 [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Açıklayan nasıl [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] görünümleri ve adreslerini hiyerarşisi.  
  
 [VSPackage’lar](../../extensibility/internals/vspackages.md)  
 VSPackage, genişleten yüklenebilir bir COM nesnesi için genel bir bakış sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ortam ve kendi VSPackage'ı uygulamak nasıl ele alınmaktadır.  
  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Projeleri kodu değiştirmek, derleme ve kod, derleme ve çalıştırma ve kod hatalarını ayıklamak için nasıl kullanılacağını açıklar ve proje türleri oluşturma konusunda ayrıntılı konulara bağlantılar sağlar.

