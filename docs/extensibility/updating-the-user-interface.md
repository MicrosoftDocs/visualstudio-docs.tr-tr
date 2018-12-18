---
title: Kullanıcı arabirimini güncelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b3bc8c4b87aefe62cbd27e64fc426ddb7abf96e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139162"
---
# <a name="updating-the-user-interface"></a>Kullanıcı arabirimi güncelleştiriliyor
Bir komut uygulandıktan sonra kullanıcı arabirimi yeni komutlarınızı durumunu güncelleştirmek için kod ekleyebilirsiniz.  
  
 Tipik bir Win32 uygulaması komut kümesini sürekli olarak sorgulandığı zamanı ve kullanıcı bunları görünümler gibi tek tek komutları durumunu ayarlanabilir. Ancak, çünkü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kabuk VSPackages sınırsız sayıda barındırabilir, kapsamlı yoklama yanıtlama hızı, yönetilen kod ve COM arasında birlikte çalışma derlemeleri arasında özellikle yoklama azaltmak  
  
### <a name="to-update-the-ui"></a>Kullanıcı arabirimini güncelleştirmek için  
  
1.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> yöntemi.  
  
         Bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi elde edilebilir gelen <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> gibi hizmet.  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Varsa parametresinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> sıfır değil (`TRUE`), güncelleştirme eş zamanlı olarak ve hemen gerçekleştirilir. Sıfır geçirdiğiniz öneririz (`FALSE`) iyi bir performans sağlamak Bu parametre için. Önbelleğe alma önlemek istiyorsanız, uygulama `DontCache` .vsct dosyasında komutu oluşturduğunuzda bayrak. Bununla birlikte, bayrağı dikkatli kullanmanız veya performansı düşebilir. Komut bayrakları hakkında daha fazla bilgi için bkz: [komutu bayrağı öğesi](../extensibility/command-flag-element.md) belgeleri.  
  
    -   Bir pencerede yerinde etkinleştirme modeli kullanarak bir ActiveX denetimini barındırmasına VSPackages kullanmak daha kullanışlı olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> yöntemi. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi ve <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> arabirimi işlevsel olarak eşdeğerdir. Her ikisi de tüm komutları durumunu yeniden sorgulamak için ortamı neden. Genellikle, bir güncelleştirmeyi hemen gerçekleştirilmez. Bunun yerine, bir güncelleştirme kadar boşta kalma süresi ertelendi. Kabuk komutu durumu iyi bir performans sağlamak için önbelleğe alır. Önbelleğe alma önlemek istiyorsanız, uygulama `DontCache` .vsct dosyasında komutu oluşturduğunuzda bayrak. Bununla birlikte, performansı düşebilir olduğundan bayrağını dikkatli kullanın.  
  
         Elde edebilirsiniz bildirimi <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> çağırarak arabirim `QueryInterface` yöntemi bir <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> nesne veya arabirimden'göre alma <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> hizmet.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanıcı arabirimi öğeleri VSPackages nasıl eklenir](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Uygulama](../extensibility/internals/command-implementation.md)