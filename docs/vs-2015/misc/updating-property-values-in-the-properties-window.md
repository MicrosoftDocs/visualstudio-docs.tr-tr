---
title: Özellikler penceresindeki özellik değerlerini güncelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 8db48e1f746afa8f8f219935555815587ce5823c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290491"
---
# <a name="updating-property-values-in-the-properties-window"></a>Özellikler penceresindeki özellik değerlerini güncelleştiriliyor
Tutmak için iki yolla **özellikleri** penceresi özellik değeri değişiklikleri ile eşitlenmiş. İlk çağırmaktır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> erişimi ve ortam tarafından sağlanan araç ve belge pencereleri oluşturma dahil, temel Pencereleme işlevleri erişim sağlayan bir arabirimi. Aşağıdaki adımlar bu eşitleme işlemi açıklar.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Ivsuıshell kullanarak özellik değerlerini güncelleştiriliyor  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Ivsuıshell arabirimini kullanarak özellik değerleri güncelleştirmek için  
  
1.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> hizmeti) bu VSPackages projeleri için istediğiniz zaman veya düzenleyicileri ihtiyaç oluşturmak veya araç veya belge pencerelerinin numaralandırmak.  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> tutmak **özellikleri** penceresini bir projenin özellik değişiklikleri ile eşitlenmiş (veya diğer tarafından konumundayken seçili nesne **özellikleri** pencere) Uygulamaolmadan<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> ve tetikleme <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> olayları.  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> yöntemleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> kurmak ve, sırasıyla uygulamak için istemci bildirimini hiyerarşi gerektirmeden hiyerarşi olayların devre dışı bırakmak için <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Iconnection kullanarak özellik değerlerini güncelleştiriliyor  
 Korumak için ikinci yol **özellikleri** özellik değeri değişiklikleri ile eşitlenmiş penceredir uygulamak için `IConnection` bağlanılabilirlik nesnesinde giden arabirimleri varlığını göstermek için. Özellik adı yerelleştirmek istiyorsanız, bir nesneden türetmek <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Uygulama döndürür özellik tanımlayıcılarının değiştirebilir ve bir özelliğin adını değiştirin. Açıklama yerelleştirmek için türetilen bir öznitelik oluşturmak <xref:System.ComponentModel.DescriptionAttribute> ve Description özelliği geçersiz.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Iconnection arabirimini uygulayan ilişkin düşünceler  
  
1.  `IConnection` Numaralandırıcı alt nesnesiyle erişim sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> arabirimi. Ayrıca tüm bağlantı noktası alt nesneleri erişim sağlar her uygulayan <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> arabirimi.  
  
2.  Herhangi bir göz atma nesne uygulamak için sorumlu olduğu bir <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> olay. **Özellikleri** penceresi aracılığıyla olay kümesi için öneri `IConnection`.  
  
3.  İsteğe bağlı olarak kaç bağlantıları (bir veya daha fazla) uygulaması içinde sağlayan bir bağlantı noktası denetimleri <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Yalnızca bir arabirim sağlayan bir bağlantı noktası döndürebilir <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> gelen <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> yöntemi.  
  
4.  Bir istemci çağırabilirsiniz `IConnection` erişmek için bir numaralandırıcı alt nesne arabirimi <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> arabirimi. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Arabirimi sonra çağrılabilir her giden arabirimi Kimliğini (IID) için bağlantı noktaları numaralandırılamadı.  
  
5.  `IConnection` bağlantı noktası alt nesneleri ile erişim sağlamak için çağrılabilir <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> giden her IID için arabirim. Aracılığıyla <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> arabirimi, bir istemci başlatır veya bağlanılabilirlik nesne ve istemcinin kendi eşitleme ile danışmanlık bir döngüyü sonlandırır. İstemci Ayrıca, çağırabilirsiniz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> bir sabit listesi nesnesi ile almak için arabirimi <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> bilir bağlantıları numaralandırmak için arabirim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme özelliği pencere seçimi ile tanışın](../misc/announcing-property-window-selection-tracking.md)   
 [Özellikleri Genişletme](../extensibility/internals/extending-properties.md)