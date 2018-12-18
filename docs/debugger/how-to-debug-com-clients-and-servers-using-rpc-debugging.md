---
title: RPC hata ayıklamasını kullanarak COM istemcilerinde ve sunucularda hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c5a6b2dc47e1d0e6c52df3cc77fc5b90f4d75e3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049033"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Nasıl Yapılır: RPC Hata Ayıklamasını Kullanarak COM İstemcilerinde ve Sunucularda Hata Ayıklama
COM istemci/sunucu uygulamalarında hata ayıklamak için uzak yordam çağrısı (RPC) hata ayıklama'ı kullanabilirsiniz. RPC kullanmak için hata ayıklamayı etkinleştirmeniz gerekir. RPC hata ayıklama etkin, hata ayıklayıcı istemciden gelen sunucu çağrı geçtiğinizde sunucuya ekler ve kendi kod hatalarını ayıklamanıza olanak tanır. Hata ayıklayıcı eklendiğinde, tüm hata ayıklama özellikleri ile istemci ve sunucu işlemlerini kullanabilirsiniz.  
  
### <a name="to-enable-rpc-debugging"></a>RPC hata ayıklamasını etkinleştirmek için  
  
1.  Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.  
  
2.  İçinde **seçenekleri** iletişim kutusu, tıklayın **hata ayıklama** klasör.  
  
3.  Tıklayın **yerel** sayfası.  
  
4.  Seçin **RPC hata ayıklama** onay kutusu.  
  
    > [!NOTE]
    >  RPC çağrıları hata ayıklamak için yönetici veya İleri kullanıcı ayrıcalıkları olmalıdır.  
  
    > [!NOTE]
    >  Yalnızca yerel bir hata ayıklayıcı uzak sunucuya bağlıysa, Microsoft Windows Vista çalıştıran bir uzak sunucuya Adımlama RPC çalışır. Aksi takdirde bir hata iletisi öykünücüsüne yönelik RPC çağrısı başarısız olur. Aksi takdirde öykünücüsüne yönelik RPC çağrısı tamamlanır, ancak step INTO öykünücüsüne yönelik RPC çağrısı çalışmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM Sunucusunda ve Kapsayıcısında Hata Ayıklama](../debugger/com-server-and-container-debugging.md)  
 [Visual Studio'da hata ayıklama](../debugger/index.md) [hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)