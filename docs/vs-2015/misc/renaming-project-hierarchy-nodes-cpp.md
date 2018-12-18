---
title: Proje hiyerarşisi düğümleri (C++) yeniden adlandırma | Microsoft Docs
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
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 5b86096834b2a841b3fe35e1045bc3897bb7667f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203768"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Yeniden adlandırma proje hiyerarşisi düğümleri (C++)
Yönetilmeyen C++ için HierUtil7 proje Çerçevesi'ni kullanarak bir proje klasörü hiyerarşisi düğümü yeniden adlandırabilirsiniz. Daha fazla bilgi için [HierUtil7 örnek](http://msdn.microsoft.com/en-us/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Hiyerarşi düğümü genişletme  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Hiyerarşi düğümü genişletin ve klasörü yeniden adlandırmak için  
  
1.  Hiyerarşi düğümü, aşağıdaki yöntemi kullanarak seçin:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` klasöre karşılık gelen hiyerarşi kapsayıcıdır ve `EXPF_SelectItem` dandır <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> sabit listesi. `GUID_MacroExplorer` Vsshell.idl içinde tanımlanmış bir GUID sabit ve bir örnek için ise `rguidPersistenceSlot` işlev imzasında `ExtExpand`Hu_node.h içinde tanımlanmış.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Hu_node.h dosyayı klasörde bulabilirsiniz \<yükleme kök > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2.  Yeniden adlandırma komutunu kullanarak yayınlayarak klasörü yeniden adlandır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` olan bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> işaretçi: `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` hangi komut grubunun benzersiz bir tanımlayıcıdır komut `cmdidRename` Vsshlids.h içinde tanımlanan ait.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje türleri oluşturma](../extensibility/internals/creating-project-types.md)   
 [VSSDK örnekleri](../misc/vssdk-samples.md)