---
title: Sınıf hiyerarşisi Simge türlerinin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8aeb208c4015d205efbfe018ee324a8ba0ede6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468869"
---
# <a name="class-hierarchy-of-symbol-types"></a>Simge Türlerinin Sınıf Hiyerarşisi
Aşağıdaki tabloda sınıf hiyerarşisi simgesi türlerini tanımlar.  
  
## <a name="symbol-types"></a>Sembol türleri  
  
|Simge türü|Açıklama|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Her sınıf, yapı ve birleşim temsil etmek için kullanılan simge.|  
|[Enum (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Numaralandırılmış türler simgesi.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|İşaretçi türleri simgesi.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Dizi türleri simgesi.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Taban türleri simgesi|  
|[Tür Tanımı (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Diğer türleri için adları tanıtır simge.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Her bir kullanıcı tanımlı tür (UDT) taban sınıfı için kullanılan simge.|  
|[Arkadaş (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Arkadaş sınıfları ve arkadaş işlevleri simgesi.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Her benzersiz işlev imzası simgesi.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Bir işlev için her bir parametreyi simgesi.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Sanal tablo boyutunu simgesi.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Sanal bir tablo simgesi.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Satıcı tanımlı tür simgesi.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Meta verilerde tanımlanan bir tür simgesi.|  
|[Boyut](../../debugger/debug-interface-access/dimension.md)|Dizi boyutları simgesi.|  
  
> [!NOTE]
>  Her simge diğer simgelerini başvurular yanı sıra simgesi hakkındaki bilgileri tutmak özelliklere sahip olabilir. Bu özellikleri tek tek sembol konuları listelenmiştir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CV_access_e numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)   
 [Simge türlerinin sözcük hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)