---
title: Proje sistemlerini genişletmeye yönelik IDE tanımlı komutlar | Microsoft Docs
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
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a58525c9b3bcbcd1bbe4792ecc9427812b62f1e1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789752"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje sistemleri genişletmek istediğinizde, komutları ve komut grupları tarafından sağlanan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Aşağıdaki bölümlerde proje sistemleri genişletmek için kullanışlı olan komut öğeleri listelenir.  
  
## <a name="command-menus"></a>Komut menüleri  
 Aşağıdaki tablo, bir proje genişletici çağırma üst düzey komutların koymak için yararlı konumlar komut menüleri gösterir.  
  
|Komutu menüsü|Açıklama|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**Proje** üst düzey menü.|  
|IDM_VS_TOOL_PROJWIN|**Çözüm Gezgini** araç çubuğu.|  
  
## <a name="shortcut-menus"></a>Kısayol menüleri  
 Aşağıdaki tabloda, tek bir düğüm olarak seçildiğinde uygulayan kısayol menülerini gösterilmektedir **Çözüm Gezgini**, veya birden çok homojen seçimleri olduğunda **Çözüm Gezgini**, ne zaman olduğu Tüm seçili düğümleri aynı türüdür.  
  
|Kısayol menüsü|Açıklama|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Proje düğümü seçildiğinde uygulanır.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Bir dosya seçili durumdayken geçerlidir.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Bir klasörü seçildiğinde uygulanır.|  
|IDM_VS_CTXT_WEBREFFOLDER|Web başvuru klasörü seçildiğinde uygulanır.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"Başvuru" adlı başvuruları kök düğümü seçildiğinde uygulanır.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Başvuru düğümleri seçili olduğunda geçerlidir; Bunlar, derleme, COM ve yalnızca proje başvurularını içerir. Web başvuruları içermez.|  
  
 Aşağıdaki tabloda, ne zaman uygulamak kısayol menüleri gösterilmektedir seçiminde **Çözüm Gezgini** yayılan birden çok hiyerarşi  
  
|Kısayol menüsü|Açıklama|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Çözüm düğümü ve kök proje düğümleri geçerli seçime içerdiğinde, geçerlidir.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Geçerli seçimi çözüm düğümü ve proje öğeleri içeren uygulanır.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Geçerli seçimi birden çok kök proje düğümden yalnızca oluşur uygulanır.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Geçerli seçimi kök proje düğümleri ve proje öğeleri bir karışımını içeren uygulanır. Ayrıca, seçim çözüm düğümüne içerebilir.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Geçerli seçimi proje öğelerinden bir çözümde birden çok proje içeriyorsa ya da farklı türdeki öğeleri aynı proje içinde seçili olduğunda geçerlidir.|  
  
## <a name="command-groups"></a>Komut grupları  
 Projeleri genişletme ve aracılığıyla erişebileceğiniz kullanabileceğiniz komut gruplarını aşağıdaki tabloda gösterilmektedir <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> kısayol menüsü.  
  
|Komut grubu|Açıklama|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Derleme, yeniden oluşturma ve projeyi dağıtma komutları.|  
|IDG_VS_CTXT_COMPILELINK|Derleme ve bağlama projesi komutlar içerir.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Proje yapılandırması ayarlayın ve derleme sırası komutları.|  
|IDG_VS_CTXT_PROJECT_ADD|Proje öğeleri Ekle komutları.|  
|IDG_VS_CTXT_PROJECT_START|F5 tuşuna ile ilişkili başlangıç projesi ayarlama komutları.|  
|IDG_VS_CTXT_PROJECT_SAVE|Proje öğeleri kaydedilirken komutlar içerir.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Hata ayıklama komutlar içerir.|  
|IDG_VS_CTXT_PROJECT_SCC|Kaynak denetimi için komutları.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Komutları için kesme, kopyalama ve yapıştırma işlemleri.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Erişim sağlayan komutlar **proje özellikleri** iletişim kutusu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md)

