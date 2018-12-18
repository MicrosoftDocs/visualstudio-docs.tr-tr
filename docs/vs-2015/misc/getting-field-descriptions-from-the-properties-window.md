---
title: Alan tanımları Özellikler penceresinden alma | Microsoft Docs
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
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: fc5d2c8553ccdb6c554f9a8364e9fd21eaa324d1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814798"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Özellikler penceresinden alan tanımlarını alma
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
  
```  
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
  
 Uygulayarak bir özelliğin açıklamasını ve yerelleştirilmiş adı alma başka bir yolu ise <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Bu yöntemin uygulanması için ilgili daha fazla bilgi için bkz. [Özellikler penceresi alanları ve arabirimleri](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Özellikler penceresi alanları ve arabirimleri](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Özellikleri genişletme](../extensibility/internals/extending-properties.md)   
 [helpstringdll](http://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [HelpString](http://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](http://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [HelpContext](http://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [HelpFile](http://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](http://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)