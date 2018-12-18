---
title: Eski API'yi kullanarak görünüm ayarlarını değiştirme | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df84fa92cb0da8dd408b1cc8717628afa3d5ba19
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730626"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Eski API'yi kullanarak görünüm ayarlarını değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sözcük kaydırma ve seçim boşluğu sanal alanı gibi temel Düzenleyici özellikleri için ayarları yoluyla kullanıcı tarafından değiştirilebilir **seçenekleri** iletişim kutusu. Ancak, aynı zamanda bu ayarları değiştirmek mümkündür programlı olarak.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Eski API'yi kullanarak ayarlarını değiştirme  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Arabirim bir metin düzenleyicisi özellik kümesi sunar. Metin görünümü için metin görünümünü programlı olarak değiştirilen ayar grubu temsil eden bir kategori özelliklerinin (GUID_EditPropCategory_View_MasterSettings) içerir. Görünüm ayarlarını bu şekilde değiştirilmiş sonra bunların içinde değiştirilemez **seçenekleri** sıfırlanana kadar iletişim kutusu.  
  
 Aşağıdaki çekirdek Düzenleyici örneği görünüm ayarlarını değiştirmek için tipik bir işlemdir.  
  
1.  Çağrı `QueryInterface` üzerinde (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> arabirimi.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> yöntemi için GUID_EditPropCategory_View_MasterSettings değerini belirterek `rguidCategory` parametresi.  
  
     Bunun yapılması, bir işaretçi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> görünüm için zorlanan bir özellikler kümesini içeren arabirimi. Bu gruptaki herhangi bir ayarı kalıcı olarak zorlanır. Bu grupta bir ayar değil sonra belirtilen seçenekleri izleyeceği **seçenekleri** iletişim kutusu veya kullanıcının komutları.  
  
3.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> yöntemi, uygun ayarları değeri belirterek `idprop` parametresi.  
  
     Örneğin, sözcük kaydırma zorlamak için çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> ve VSEDITPROPID_ViewLangOpt_WordWrap, bir değer belirleyebilirsiniz `vt` için `idprop` parametresi. Bu çağrıda `vt` VT_BOOL türünde bir değişken olduğu ve `vt.boolVal` VARIANT_TRUE olduğu.  
  
## <a name="resetting-changed-view-settings"></a>Değiştirilen görünüm ayarlarını sıfırlama  
 Tüm değiştirilmiş görünüm çekirdek Düzenleyici örneği için ayarını sıfırlamak için çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> yöntemi ve uygun ayar değeri belirtin `idprop` parametresi.  
  
 Örneğin, sözcük kaydırma serbestçe kaydırmak izin vermek için özellik kategorisinden çağırarak kaldırmadan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> VSEDITPROPID_ViewLangOpt_WordWrap için değerini belirterek `idprop` parametresi.  
  
 Değişen tüm çekirdek Düzenleyici ayarlarını kaldırmak için VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, için vt değerini belirtirseniz `idprop` parametresi. Bu çağrı içinde vt VT_BOOL türünde bir değişken ve vt.boolVal VARIANT_TRUE şeklindedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek Düzenleyicisi içinde](../extensibility/inside-the-core-editor.md)   
 [Eski API'yi kullanarak erişen erişimcisinde görüntüle](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Seçenekler İletişim Kutusu](../ide/reference/options-dialog-box-visual-studio.md)

