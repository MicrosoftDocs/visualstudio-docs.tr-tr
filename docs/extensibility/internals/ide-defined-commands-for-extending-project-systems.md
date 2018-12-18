---
title: Proje sistemleri genişletmek için komutları IDE tanımlı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4941f5d842f311f078594ee9a9deef02219ea05d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132021"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Proje sistemleri genişletme IDE tanımlı komutları
Proje sistemleri genişletmek istediğiniz zaman, komutları kullanın ve komut tarafından sağlanan grupları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Aşağıdaki bölümlerde proje sistemleri genişletmek için özellikle yararlı komut öğeleri listeleyin.  
  
## <a name="command-menus"></a>Komut menüleri  
 Aşağıdaki tabloda, proje genişletici çağırma üst düzey komutların yerleştirmek yararlı konumlarının komutu menüleri gösterir.  
  
|Komut menüsü|Açıklama|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**Proje** en üst düzey menü.|  
|IDM_VS_TOOL_PROJWIN|**Çözüm Gezgini** araç.|  
  
## <a name="shortcut-menus"></a>Kısayol menüleri  
 Aşağıdaki tabloda, tek bir düğüm seçildiğinde, geçerli kısayol menüleri gösterilmektedir **Çözüm Gezgini**, veya birden çok homojen seçimleri olduğunda **Çözüm Gezgini**, ne zaman olduğu Seçili tüm düğümler aynı türüdür.  
  
|Kısayol menüsü|Açıklama|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Proje düğümüne seçili olduğunda geçerlidir.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Bir dosya seçili olduğunda geçerlidir.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Bir klasörü seçildiğinde uygulanır.|  
|IDM_VS_CTXT_WEBREFFOLDER|Web başvurusu klasörü seçildiğinde uygulanır.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"Başvurular" olarak adlandırılan başvurular kök düğümü seçildiğinde uygulanır.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Başvuru düğümleri seçili olduğunda geçerlidir; Bunlar, derleme, COM ve yalnızca proje başvuruları içerir. Web başvuruları içermez.|  
  
 Aşağıdaki tabloda, ne zaman uygulamak kısayol menüleri gösterilmektedir seçim **Çözüm Gezgini** birden çok hiyerarşi yayılan  
  
|Kısayol menüsü|Açıklama|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Geçerli seçim çözüm düğümüne ve kök proje düğümlerini içeren uygulanır.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Geçerli seçim çözüm düğümü ve proje öğeleri içerdiğinde geçerlidir.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Geçerli seçim birden çok kök proje düğümden yalnızca oluşur uygulanır.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Geçerli seçim kök proje düğümler ve proje öğeleri bir karışımını içeren uygulanır. Ayrıca, seçim çözüm düğümüne içerebilir.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Geçerli seçim birden çok proje çözümü proje öğelerinden içerdiğinde ya da farklı türdeki öğeler için aynı projede seçili olduğunda geçerlidir.|  
  
## <a name="command-groups"></a>Komut grupları  
 Aşağıdaki tabloda projeleri genişletme ve üzerinden erişebilirsiniz kullanabileceğiniz komut gruplarını gösterir <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> kısayol menüsü.  
  
|Komut grubu|Açıklama|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Oluşturma, yeniden oluşturma ve projeyi dağıtmak için komutları.|  
|IDG_VS_CTXT_COMPILELINK|Derleme ve projeyi bağlama için komutları.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Proje yapılandırması ayarlayın ve derleme sırası komutları.|  
|IDG_VS_CTXT_PROJECT_ADD|Proje öğeleri Ekle komutları.|  
|IDG_VS_CTXT_PROJECT_START|F5 anahtar ile ilişkili başlangıç projesi ayarlama komutları.|  
|IDG_VS_CTXT_PROJECT_SAVE|Proje öğeleri kaydetmek için komutları.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Hata ayıklama için komutları.|  
|IDG_VS_CTXT_PROJECT_SCC|Kaynak denetimi için komutları.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Komutları için kesme, kopyalama ve yapıştırma işlemleri.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Erişim sağlayan komutlar **proje özelliklerini** iletişim kutusu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanıcı arabirimi öğeleri VSPackages nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md)