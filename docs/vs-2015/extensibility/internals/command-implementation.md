---
title: Komut, uygulama | Microsoft Docs
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
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be1bcecb740fb0c375d0f461639a8b0d5e40669a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765196"
---
# <a name="command-implementation"></a>Komut Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Komut içinde bir VSPackage'ı uygulamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:  
  
1. .Vsct dosyası bir komut grubu ayarlayın ve komut ekleyin. Daha fazla bilgi için [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Komutu, Visual Studio ile kaydedin.  
  
3. Komut uygulayın.  
  
   Aşağıdaki bölümlerde, kaydetme ve komutları uygulamak açıklanmaktadır.  
  
## <a name="registering-commands-with-visual-studio"></a>Visual Studio ile komutları kaydediliyor  
 Komutunuz menüde görünmesini olması durumunda eklemeniz gerekir <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage ve menünün adını veya kaynak kimliğini değeri olarak kullanın  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Ayrıca, komut ile kaydetmelisiniz <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Bu hizmeti kullanarak alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> , VSPackage türetilir, yöntemi <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Uygulama komutları  
 Çeşitli komutları uygulamak için yollar vardır. Her zaman aynı şekilde ve aynı menüsünde görünen komut olan statik menü komutu, isterseniz komutu kullanarak oluşturma <xref:System.ComponentModel.Design.MenuCommand> önceki bölümdeki örneklerde gösterildiği gibi. Statik bir komut oluşturmak için bu komutu yürütmek için sorumlu olduğu bir olay işleyicisi sağlamanız gerekir. Komut, her zaman etkin ve görünür olduğundan, durumu sağlamak için Visual Studio gerekmez. Belirli koşullara bağlı olarak bir komutun durumunu değiştirmek istiyorsanız, komutu bir örneği oluşturabilir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıfı ve komutu yürütmek için bir olay işleyicisi ve görsel bildirmek için bir sorgu durumu işleyicisi oluşturucusunda, sağlayın Komutun durumunu değiştirdiğinde studio. Ayrıca uygulayabilirsiniz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut sınıfı veya, bir parçası uygulayabilirsiniz gibi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projenin bir parçası bir komut sağlıyorsanız. İki arabirim ve <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıfı tüm Visual Studio bir komutun durumunu değişikliği bildirim yöntemleri ve komutun yürütülmesini sağlayan diğer yöntemler vardır.  
  
 Bir komut komut hizmetine eklendiğinde, bir komut zinciri olur. Komut durumu bildirimi ve yürütme yöntemleri uygularken, yalnızca belirli bu komut için sağlamak ve diğer tüm durumlarda diğer komutlar açın zincirinde geçirmek için dikkatli olun. Komut geçirilecek başarısız olursa (döndürerek genellikle <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio düzgün çalışmasını durdurabilir.  
  
## <a name="query-status-methods"></a>Sorgu durumu yöntemleri  
 Ya da uyguluyorsanız <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> yöntemi, denetimi Ayarla komutu ait olduğu komutun GUID ve komut kimliği. Aşağıdaki yönergeleri izleyin:  
  
- GUID, tanınmıyor, uygulamanız her iki yöntem döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Her iki yöntem uygulamanıza GUID tanır, ancak gerçekte komutu uygulamadı durumunda yöntem döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Her iki yöntem uygulamanıza GUID hem komutu tanır sonra yöntem, her komut komut bayrakları alanı ayarlamanız gerekir (içinde `prgCmds` parametresi) aşağıdaki bayraklar kullanarak:  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> komut destekleniyorsa.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> komutun görünür olmamalıdır.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Komut çubuğunda açılıp ve sahip gibi görünüyor, iade.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> komut etkinse.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> kısayol menüsünde görünen komut gizli.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> komut bir menü denetleyicisi ve etkin değil, ancak aşağı açılan listesinin boş değil ve hala kullanılabilir olması gerekir. (Bu bayrağı nadiren kullanılır.)  
  
- Komutu ile .vsct dosyası içinde tanımlanmışsa, `TextChanges` bayrağı, aşağıdaki parametreleri ayarlayın:  
  
  -   Ayarlama `rgwz` öğesinin `pCmdText` yeni metin komut parametresi.  
  
  -   Ayarlama `cwActual` öğesinin `pCmdText` komut dize boyutu parametresi.  
  
  Ayrıca, komut Otomasyon işlevleri işlemek için özellikle tasarlanmıştır sürece geçerli bağlam bir Otomasyon işlevi olmadığından emin olun.  
  
  Belirli bir komut desteklediğini göstermek için dönüş <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Diğer tüm komutlar için iade <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
  Aşağıdaki örnekte, sorgu durumu yöntemi önce bağlamı bir Otomasyon işlev değil ve ardından komut kimliği ve doğru komut kümesi GUID bulur emin olur Komut, desteklenen ve etkinleştirilmesi için ayarlanır. Diğer bir komutlar desteklenir.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Yürütme yöntemi  
 Uygulama yürütme yönteminin sorgu durumu yöntemin uygulanmasını benzer. İlk olarak, bağlam Otomasyon işlevi olmadığından emin olun. Ardından test GUID hem komut kimliği. GUID ya da komut kimliği tanınmıyor, iade <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Komutunu işlemek için onu yürütmek ve dönüş <xref:Microsoft.VisualStudio.VSConstants.S_OK> yürütme başarılı olursa. Komutu, hata algılama ve bildirim sorumludur; Bu nedenle, yürütme başarısız olursa hata kodunu döndürür. Aşağıdaki örnek, yürütme yöntemi nasıl uygulanması gösterir.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

