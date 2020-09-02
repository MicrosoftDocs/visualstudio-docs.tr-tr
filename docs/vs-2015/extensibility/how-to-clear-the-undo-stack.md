---
title: 'Nasıl yapılır: geri alma yığınını temizleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db77f93fd7f6af16b5358b75b6ffcd5927430653
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62549187"
---
# <a name="how-to-clear-the-undo-stack"></a>Nasıl Yapılır: Geri Alma Yığınını Temizleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki yordamda geri alma yığınının nasıl temizleneceği açıklanmaktadır.  
  
### <a name="to-clear-the-undo-stack"></a>Geri alma yığınını temizlemek için  
  
1. Geri alma yığınını temizlemek için, [IOleUndoManager::D SCC](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) ' i kullanın. Aşağıda buna bir örnek verilmiştir:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Geri Alma Yönetimini Uygulama](../extensibility/how-to-implement-undo-management.md)
