---
title: Program düğümleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc87a24b35993f200c709ee033fffe6a4ecb120
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903627"
---
# <a name="program-nodes"></a>Program düğümleri
Hata ayıklayıcı mimarisinde bir *program düğüm*:  
  
- Basit bir program açıklamasıdır.  
  
- Kendisi ve onu çalışan işlemi tanımlayabilirsiniz. Öğesinden ayrıldı ve varsa, oluşturulan hata ayıklama altyapısı (DE) tanımlamak için bir program düğümü eklenebilir.  
  
- Tarafından temsil edilen bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi, genellikle DE veya bağlantı noktası tarafından oluşturulur. Program düğümleri çağırarak bir bağlantı noktasına eklenir [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Bir program düğüm bir bağlantı eklendiğinde bu programı bu düğümün temsil ettiği program içeren işleme eklenir.  
  
  Süre bir hata ayıklama oturumu, hata ayıklama paketi bağlı olarak uygulama başlatıldıktan sonra program düğümleri karşılık gelen programlar oluşturmak için kullanılır. Bir işlem için programları sorgulandığında programları numaralandırılır, program her düğüm için bir tane.  
  
  Bir program iliştirildiği önce IDE program basit bir açıklamasını gerekir. Bu bilgi programı düğümden elde edilebilir. Program için bağlandıktan sonra IDE programdaki tüm iş parçacıkları listesi gibi daha ayrıntılı bilgileri görüntüler. Bu bilgiler programından elde edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Programlar](../../extensibility/debugger/programs.md)   
 [İşlemler](../../extensibility/debugger/processes.md)   
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)