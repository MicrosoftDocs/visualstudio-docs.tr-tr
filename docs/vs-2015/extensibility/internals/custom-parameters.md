---
title: Özel Parametreler | Microsoft Docs
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
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8bb8a1861d6162e73906d74250f738ff96b9a505
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757907"
---
# <a name="custom-parameters"></a>Özel Parametreler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir sihirbaz başlatıldıktan sonra özel parametreler sihirbaz işlemi denetleyin. İlgili .vsz dosyası, kullanıcı tanımlı olan tümleşik geliştirme ortamı (IDE) paketlenir ve Sihirbazı başlattığınızda sihirbaz dize dizisi geçirilen parametreler dizisi sağlar. Sihirbaz dizisini ayrıştırır ve gerçek işlem sihirbazın denetlemek için bu bilgileri kullanır. Bu şekilde, bir sihirbaz .vsz dosyasının içeriğini bağlı olarak işlevsellik özelleştirebilirsiniz.  
  
 Sihirbazı başlattığınızda bağlam parametreleri, diğer taraftan, proje durumunu tanımlar. Daha fazla bilgi için [bağlam parametreleri](../../extensibility/internals/context-parameters.md).  
  
 Özel Parametreler içeren bir .vsz dosyası örneği aşağıdadır:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz dosyası yazarı parametrelerinin değerlerini ekler. Bir kullanıcı seçtiğinde **yeni proje** veya **Yeni Öğe Ekle** Dosya menüsünden veya bir projeye sağ tıklayarak **Çözüm Gezgini**, IDE bu değerleri dizisi toplar. dizeleri. IDE sonra projenin çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> yöntemiyle <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> bayrak kümesi ve proje çağrıları <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> Sihirbazı'nı çalıştıran ve sonucu döndürerek sorumlu yöntemi.  
  
 Sihirbaz, dize dizisi, ayrıştırma ve dizeleri uygun şekilde hareket sorumludur. Özel Parametreler uygulayarak bu şekilde, çeşitli işlevler gerçekleştiren bir sihirbaz oluşturabilirsiniz. Diğer bir deyişle, bir sihirbaz üç farklı .vsz dosyası olabilir. Her dosya, farklı çeşitli durumlarda sihirbazda davranışını denetlemek için özel parametreleri kümesini geçirir.  
  
 Daha fazla bilgi için [Sihirbazı (. Vsz) dosya](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)   
 [Sihirbazlar](../../extensibility/internals/wizards.md)   
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)

