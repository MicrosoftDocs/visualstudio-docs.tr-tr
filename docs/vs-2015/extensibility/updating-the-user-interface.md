---
title: Kullanıcı arabirimini güncelleştirme | Microsoft Docs
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
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4e6b282ac58e523e8a2047e7f882d90b9f202bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765547"
---
# <a name="updating-the-user-interface"></a>Kullanıcı Arabirimini Güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir komut uyguladıktan sonra yeni komutlarınızı durumuyla kullanıcı arabirimini güncelleştirmek için kod ekleyebilirsiniz.  
  
 Tipik bir Win32 uygulaması komut kümesi sürekli olarak yoklanabilir ve bunları kullanıcı görünümleri gibi tek tek komutlarla durumunu ayarlanabilir. Ancak, çünkü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kabuk VSPackages sınırsız sayıda barındırabilir, kapsamlı yoklama arasında birlikte çalışma bütünleştirilmiş kodları com ile yönetilen kod arasındaki özellikle yoklama yanıt verme hızını Azalt  
  
### <a name="to-update-the-ui"></a>Kullanıcı arabirimini güncelleştirmek için  
  
1.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> yöntemi.  
  
         Bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi elde edilebilir gelen <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> hizmeti, aşağıdaki gibi.  
  
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
  
         Varsa parametresi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> sıfır değil (`TRUE`), güncelleştirme, zaman uyumlu ve hemen gerçekleştirilir. Sıfır geçmesini öneririz (`FALSE`) iyi bir performans sağlamak Bu parametre için. Önbelleğe alma önlemek istiyorsanız, geçerli `DontCache` .vsct dosyası içinde komut oluşturduğunuzda bayrak. Bununla birlikte, bayrağı dikkatli ya da performans düşebilir. Komut bayrakları hakkında daha fazla bilgi için bkz: [Command Flag öğesi](../extensibility/command-flag-element.md) belgeleri.  
  
    -   Bir pencere içinde yerinde etkinleştirme modeli kullanarak bir ActiveX denetimini barındırmak Vspackage'larda kullanmak daha kullanışlı olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> yöntemi. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi ve <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> arabirimi işlevsel olarak eşdeğerdir. Her ikisi de yeniden tüm komutları durumunu sorgulamak için ortamı neden. Genellikle, bir güncelleştirmeyi hemen gerçekleştirilmez. Bunun yerine, bir güncelleştirme boşta kalma süresi kadar geciktirilir. Kabuk komut durumu iyi bir performans sağlamak için önbelleğe alır. Önbelleğe alma önlemek istiyorsanız, geçerli `DontCache` .vsct dosyası içinde komut oluşturduğunuzda bayrak. Bununla birlikte, performansı düşürebilir, çünkü bayrağı dikkatli kullanın.  
  
         Edinebileceğiniz bildirimi <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> çağırarak arabirim `QueryInterface` metodunda bir <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> nesne veya arabirimden'göre edinme <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> hizmet.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Uygulama](../extensibility/internals/command-implementation.md)

