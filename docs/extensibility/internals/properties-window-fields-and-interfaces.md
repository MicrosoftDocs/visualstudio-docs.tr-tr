---
title: Özellikler penceresi alanları ve arabirimleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 149c02918ec909c03c1102a5fc0f1643b79fb46d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883412"
---
# <a name="properties-window-fields-and-interfaces"></a>Özellikler Penceresi Alanları ve Arabirimleri
Seçim, hangi bilgilerin görüntüleneceğini belirlemek modelin **özellikleri** penceresi odaklı IDE'de pencerenin temel alır. Her pencere ve seçili penceresi içinde nesne genel seçimi bağlamına gönderildi, Seçim bağlam nesnesi olabilir. Bu pencere odaklandığında ortamı genel seçim bağlamını pencere çerçevesi değerlerini güncelleştirir. Bu nedenle odağı değiştiğinde seçim bağlamını yapar.  
  
## <a name="tracking-selection-in-the-ide"></a>IDE'de seçim izleme  
 Pencere çerçevesi veya site, IDE tarafından sahip olunan adlı bir hizmet olan <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Bir değişiklik nasıl bir kullanıcı başka bir açık penceresine odak değiştirme ya da farklı proje öğesinde seçerek kaynaklanan bir seçimi aşağıdaki adımları Göster **Çözüm Gezgini**, içindegörüntüleneniçerikdeğiştirmekiçinuygulanır **Özellikleri** penceresi.  
  
1. Seçilen pencere çağrılarında tarihli VSPackage'ı tarafından oluşturulan nesne <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> olmasını <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> çağırma <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Seçilen pencere tarafından sağlanan seçim kapsayıcısı kendi oluşturur <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesne. Seçim değişiklikleri VSPackage çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ortamında, tüm dinleyici bildirmek için de dahil olmak üzere **özellikleri** pencerenin Değiştir. Ayrıca, yeni seçime ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.  
  
3. Çağırma <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ve Seçili hiyerarşiyi öğeleri geçirerek `VSHPROPID_BrowseObject` parametresi doldurur <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesne.  
  
4. Türetilen bir nesne [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) için döndürülen <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> İstenen öğe ve ortam içine sarmalar bir <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (bkz. aşağıdaki adım). Çağrı başarısız olursa ortam ikinci çağrıda `IVsHierarchy::GetProperty`, seçim kapsayıcısı geçirme <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> hiyerarşi öğesi veya öğelerini sağlayın.  
  
    VSPackage oluşturmaz, projenizi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ortamı tarafından sağlanan penceresi VSPackage, onu uyguladığından (örneğin, **Çözüm Gezgini**) yapıları <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> kendi adına.  
  
5. Ortam yöntemlerini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesneleri göre almak için `IDispatch` doldurun için arabirim **özellikleri** penceresi.  
  
   Bir değer olduğunda **özellikleri** penceresi değiştirildiğinde, VSPackages uygulamak `IVsTrackSelectionEx::OnElementValueChangeEx` ve `IVsTrackSelectionEx::OnSelectionChangeEx` değişikliği için öğe değeri bildirmek için. Ardından ortamın çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> veya <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> görüntülenen bilgileri tutmak **özellikleri** pencereyi eşzamanlı özellik değerleri. Daha fazla bilgi için [Özellikler penceresindeki özellik değerlerini güncelleştirme](#updating-property-values-in-the-properties-window).  
  
   Farklı bir seçmenin yanı sıra içinde proje öğesi **Çözüm Gezgini** öğeyle ilişkili özellikleri görüntülemek için de kullanılabilir aşağı açılan listeyi kullanarak bir form veya belge penceresi içinde farklı bir nesne seçebilirsiniz **Özellikleri** penceresi. Daha fazla bilgi için [Özellikler penceresi nesne listesi](../../extensibility/internals/properties-window-object-list.md).  
  
   Bilgi görüntülendiği şekilde değiştirebilirsiniz **özellikleri** penceresi kılavuzdan alfabetik kategorik için ve kullanılabilir olması durumunda da seçilen bir nesne için bir özellik sayfası üzerindeuygundüğmeleretıklayarakaçabilirsiniz **Özellikleri** penceresi. Daha fazla bilgi için [Özellikler penceresi düğmeleri](../../extensibility/internals/properties-window-buttons.md) ve [özellik sayfaları](../../extensibility/internals/property-pages.md).  
  
   Son olarak, listenin sonuna **özellikleri** penceresinde de seçilen alanın açıklaması bulunur **özellikleri** pencere kılavuzunun. Daha fazla bilgi için [alma alan açıklamaları Özellikler penceresinden](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a> Özellikler penceresindeki özellik değerlerini güncelleştiriliyor
Tutmak için iki yolla **özellikleri** penceresi özellik değeri değişiklikleri ile eşitlenmiş. İlk çağırmaktır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> erişimi ve ortam tarafından sağlanan araç ve belge pencereleri oluşturma dahil, temel Pencereleme işlevleri erişim sağlayan bir arabirimi. Aşağıdaki adımlar bu eşitleme işlemi açıklar.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Ivsuıshell kullanarak özellik değerlerini güncelleştiriliyor  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Ivsuıshell arabirimini kullanarak özellik değerleri güncelleştirmek için  
  
1.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> hizmeti) bu VSPackages projeleri için istediğiniz zaman veya düzenleyicileri ihtiyaç oluşturmak veya araç veya belge pencerelerinin numaralandırmak.  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> tutmak **özellikleri** penceresini bir projenin özellik değişiklikleri ile eşitlenmiş (veya diğer tarafından konumundayken seçili nesne **özellikleri** pencere) Uygulamaolmadan<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> ve tetikleme <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> olayları.  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> yöntemleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> kurmak ve, sırasıyla uygulamak için istemci bildirimini hiyerarşi gerektirmeden hiyerarşi olayların devre dışı bırakmak için <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Iconnection kullanarak özellik değerlerini güncelleştiriliyor  
 Korumak için ikinci yol **özellikleri** özellik değeri değişiklikleri ile eşitlenmiş penceredir uygulamak için `IConnection` bağlanılabilirlik nesnesinde giden arabirimleri varlığını göstermek için. Özellik adı yerelleştirmek istiyorsanız, bir nesneden türetmek <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Uygulama döndürür özellik tanımlayıcılarının değiştirebilir ve bir özelliğin adını değiştirin. Açıklama yerelleştirmek için türetilen bir öznitelik oluşturmak <xref:System.ComponentModel.DescriptionAttribute> ve Description özelliği geçersiz.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Iconnection arabirimini uygulayan ilişkin düşünceler  
  
1.  `IConnection` Numaralandırıcı alt nesnesiyle erişim sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> arabirimi. Ayrıca tüm bağlantı noktası alt nesneleri erişim sağlar her uygulayan <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> arabirimi.  
  
2.  Herhangi bir göz atma nesne uygulamak için sorumlu olduğu bir <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> olay. **Özellikleri** penceresi aracılığıyla olay kümesi için öneri `IConnection`.  
  
3.  İsteğe bağlı olarak kaç bağlantıları (bir veya daha fazla) uygulaması içinde sağlayan bir bağlantı noktası denetimleri <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Yalnızca bir arabirim sağlayan bir bağlantı noktası döndürebilir <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> gelen <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> yöntemi.  
  
4.  Bir istemci çağırabilirsiniz `IConnection` erişmek için bir numaralandırıcı alt nesne arabirimi <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> arabirimi. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Arabirimi sonra çağrılabilir her giden arabirimi Kimliğini (IID) için bağlantı noktaları numaralandırılamadı.  
  
5.  `IConnection` bağlantı noktası alt nesneleri ile erişim sağlamak için çağrılabilir <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> giden her IID için arabirim. Aracılığıyla <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> arabirimi, bir istemci başlatır veya bağlanılabilirlik nesne ve istemcinin kendi eşitleme ile danışmanlık bir döngüyü sonlandırır. İstemci Ayrıca, çağırabilirsiniz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> bir sabit listesi nesnesi ile almak için arabirimi <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> bilir bağlantıları numaralandırmak için arabirim.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a> Özellikler penceresinden alan tanımlarını alma
Sayfanın alt kısmında **özellikleri** penceresinde bir açıklama alanını seçili özellik alanıyla ilgili bilgileri görüntüler. Bu özellik varsayılan olarak etkinleştirilir. Açıklama alanı gizlemek istiyorsanız, sağ **özellikleri** penceresini açın ve **açıklama**. Bunun yapılması ayrıca kaldırır onay işaretinin yanındaki **açıklama** menü penceresinin başlık. Geçiş yapmak için aynı adımları izleyerek alanı yeniden görüntüleyebilirsiniz **açıklama** yeniden açın.  
  
 Açıklama alanı bilgileri geldiği <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Her yöntem, arabirim, coclass'ı ve benzeri bir yerelleştirilmemiş olabilir `helpstring` tür kitaplığında özniteliği. **Özellikleri** penceresi alır dizeden <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Yerelleştirilmiş Yardım dizeleri belirtmek için  
  
1. Ekleme `helpstringdll` özniteliği tür kitaplığının Kitaplık ifadeye (`typelib`).  
  
   > [!NOTE]
   >  Bu adım, bir nesne kitaplığı (.olb) dosyasında tür kitaplığı ise isteğe bağlıdır.  
  
2. Belirtin `helpstringcontext` dizeleri için öznitelikler. Ayrıca belirtebileceğiniz `helpstring` öznitelikleri.  
  
    Bu öznitelikler kodundan `helpfile` ve `helpcontext` gerçek .chm dosya Yardım konularında bulunan öznitelikler.  
  
   Vurgulanan özellik adı, görüntülenecek açıklama bilgileri almak için **özellikleri** penceresi çağrıları <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> seçili özellik için istenen belirtme `lcid` için öznitelik Çıkış dizesi. Dahili olarak <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> .dll dosyası içinde belirtilen bulur `helpstringdll` özniteliği ve çağrıları `DLLGetDocumentation` , .dll dosyasında belirtilen bağlamla ve `lcid` özniteliği.  
  
   Uygulamasını ve imza `DLLGetDocumentation` şunlardır:  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` DLL için .def dosyasında tanımlanmış bir dışarı aktarma işlevi olmalıdır.  
  
 Dahili olarak, aslında DLL olduğu bir .olb dosyası oluşturulur. Bir kaynak, tür kitaplığı (.tlb) dosyasını ve dışarı aktarılan bir işlevin bu DLL içeren `DLLGetDocumentation`.  
  
 .Olb dosyalar, söz konusu olduğunda `helpstringdll` .tlb dosyasının kendisini içeren aynı dosya olduğu için özniteliği isteğe bağlıdır.  
  
 Dizeleri görünmesini almak için **açıklamaları** bölmesinde, bu nedenle, yapmanız gereken en düşük belirtin `helpstring` tür kitaplığında özniteliği. Bu dizelerin yerelleştirilmesi istiyorsanız belirtmek zorunda `helpstringdll` (isteğe bağlı) özniteliği ve `helpstringcontext` (gerekli) özniteliği ve uygulamanıza `DLLGetDocumentation`.  
  
 IDL'ın aracılığıyla bilgi başlama yerelleştirilmiş uygulanması gereken ek arabirimi yok `helpstringcontext` özniteliği ve `DLLGetDocumentation`.  
  
 Uygulayarak bir özelliğin açıklamasını ve yerelleştirilmiş adı alma başka bir yolu ise <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Bu yöntemin uygulanması için ilgili daha fazla bilgi için bkz. [Özellikler penceresi alanları ve arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)