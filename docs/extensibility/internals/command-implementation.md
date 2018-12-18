---
title: Komut, uygulama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f002e660b2c3b745e4a7ea67f715b613b96bd0a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510445"
---
# <a name="command-implementation"></a>Komut uygulama
Komut içinde bir VSPackage'ı uygulamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:  
  
1.  İçinde *.vsct* dosya, bir komut grubu oluşturun ve komut ekleyin. Daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).
  
2.  Komutu, Visual Studio ile kaydedin.  
  
3.  Komut uygulayın.  
    
Aşağıdaki bölümlerde, kaydetme ve komutları uygulamak açıklanmaktadır.  
  
## <a name="register-commands-with-visual-studio"></a>Visual Studio ile kayıt komutları  
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
  
## <a name="implement-commands"></a>Uygulama komutları  
 Çeşitli komutları uygulamak için yollar vardır. Her zaman aynı şekilde ve aynı menüsünde görünen komut olan statik menü komutu, isterseniz komutu kullanarak oluşturma <xref:System.ComponentModel.Design.MenuCommand> önceki bölümdeki örneklerde gösterildiği gibi. Statik bir komut oluşturmak için bu komutu yürütmek için sorumlu olduğu bir olay işleyicisi sağlamanız gerekir. Komut, her zaman etkin ve görünür olduğundan, durumu sağlamak için Visual Studio gerekmez. Belirli koşullara bağlı olarak bir komutun durumunu değiştirmek istiyorsanız, komutu bir örneği oluşturabilir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıfı ve komutu yürütmek için bir olay işleyicisi oluşturucusunda, sağlamak ve bir `QueryStatus` Visual bildirmek için işleyici Komutun durumunu değiştirdiğinde studio. Ayrıca uygulayabilirsiniz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut sınıfı veya, bir parçası uygulayabilirsiniz gibi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projenin bir parçası bir komut sağlıyorsanız. İki arabirim ve <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıfı tüm Visual Studio bir komutun durumunu değişikliği bildirim yöntemleri ve komutun yürütülmesini sağlayan diğer yöntemler vardır.  
  
 Bir komut komut hizmetine eklendiğinde, bir komut zinciri olur. Komut durumu bildirimi ve yürütme yöntemleri uygularken, yalnızca belirli bu komut için sağlamak ve diğer tüm durumlarda diğer komutlar açın zincirinde geçirmek için dikkatli olun. Komut geçirilecek başarısız olursa (döndürerek genellikle <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio düzgün çalışmasını durdurabilir.  
  
## <a name="querystatus-methods"></a>QueryStatus yöntemleri  
 Ya da uyguluyorsanız <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> yöntemi, denetimi Ayarla komutu ait olduğu komutun GUID ve komut kimliği. Aşağıdaki yönergeleri izleyin:  
  
-   GUID, tanınmıyor, uygulamanız her iki yöntem döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Her iki yöntem uygulamanıza GUID tanır, ancak komut uygulamadı durumunda yöntem döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Her iki yöntem uygulamanıza GUID hem komutu tanır sonra yöntem, her komut komut bayrakları alanı ayarlamanız gerekir (içinde `prgCmds` parametresi) aşağıdaki kullanarak <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> bayraklar:  
  
    -   `OLECMDF_SUPPORTED`: Komut desteklenir.  
  
    -   `OLECMDF_INVISIBLE`: Komut görünür olmamalıdır.  
  
    -   `OLECMDF_LATCHED`: Komut, üzerinde açılıp ve denetlendi gibi görünüyor.  
  
    -   `OLECMDF_ENABLED`: Komut etkin.  
  
    -   `OLECMDF_DEFHIDEONCTXTMENU`: Kısayol menüsünde görünmüyorsa komut gizlenmelidir.  
  
    -   `OLECMDF_NINCHED`: Komut menü denetleyicisi ve etkin değil ancak aşağı açılan listesinin boş değil ve yine de kullanılabilir. (Bu bayrağı nadiren kullanılır.)  
  
-   Komut içinde tanımlanmışsa *.vsct* ile dosya `TextChanges` bayrağı, aşağıdaki parametreleri ayarlayın:  
  
    -   Ayarlama `rgwz` öğesinin `pCmdText` yeni metin komut parametresi.  
  
    -   Ayarlama `cwActual` öğesinin `pCmdText` komut dize boyutu parametresi.  
  

Ayrıca, komutunuzu Otomasyon işlevleri işlemek için özellikle tasarlanmıştır sürece geçerli bağlam bir Otomasyon işlevi olmadığından emin olun.  
  
Belirli bir komut desteklediğini göstermek için dönüş <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Diğer tüm komutlar için iade <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
Aşağıdaki örnekte, `QueryStatus` yöntemi ilk sağlar bağlamı bir Otomasyon işlev değil ve ardından doğru komut kümesi GUID ve komut kimliği. Komut, desteklenen ve etkinleştirilmesi için ayarlanır. Diğer bir komutlar desteklenir.  
  
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
 Uygulamasını `Exec` yöntemi uygulaması benzer `QueryStatus` yöntemi. İlk olarak, bağlam Otomasyon işlevi olmadığından emin olun. Ardından, test GUID hem komut kimliği. GUID ya da komut kimliği tanınmıyor, iade <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)