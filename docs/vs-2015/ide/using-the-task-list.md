---
title: Görev listesini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5662aebeb0e7b8da36c52c0c9fd727c860a4221
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172035"
---
# <a name="using-the-task-list"></a>Görev Listesini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanma **görev listesi** gibi belirteçler kullanan kod açıklamaları izlemek için `TODO` ve `HACK`, ya da özel belirteçler ve sizi doğrudan kod içinde önceden tanımlanmış bir konuma götürecek kısayolları yönetmek için. Kaynak kodu konumuna gitmek için liste öğesine tıklayın.  
  
 Bu konuda:  
  
-   [Görev Listesi penceresi](../ide/using-the-task-list.md#taskListWindow)  
  
-   [Kullanıcı görevleri](../ide/using-the-task-list.md#userTasks)  
  
-   [Belirteçler ve açıklamalar](../ide/using-the-task-list.md#tokensComments)  
  
-   [Özel belirteçler](../ide/using-the-task-list.md#customTokens)  
  
-   [C++ TODO açıklamaları](../ide/using-the-task-list.md#cppComments)  
  
-   [Kısayolları](../ide/using-the-task-list.md#shortcuts)  
  
##  <a name="taskListWindow"></a> Görev Listesi penceresi  
 Zaman **görev listesi** olan açık, uygulama penceresinin altında görünür.  
  
#### <a name="to-open-the-task-list"></a>Görev Listesi'ni açmak için  
  
-   Üzerinde **görünümü** menüsünde seçin **görev listesi** (klavye: Ctrl +\\, T).  
  
     ![Görev Listesi penceresi](../ide/media/vs2015-task-list.png "vs2015_task_list")  
  
#### <a name="to-change-the-sort-order-of-the-list"></a>Listenin sıralama düzenini değiştirmek için  
  
-   Herhangi bir sütunun başlığına tıklayın. Arama sonuçlarınızı iyice daraltmak için Shift tuşuna basın ve ikinci bir sütun başlığına tıklayın.  
  
     Alternatif olarak, kısayol menüsünden seçin **sıralama ölçütü**, bir başlığı seçin. Arama sonuçlarınızı iyice daraltmak için Shift tuşuna basın ve ikinci bir başlık seçin.  
  
#### <a name="to-show-or-hide-columns"></a>Sütunları göstermek veya gizlemek için  
  
-   Kısayol menüsünde **sütunları göster**. Göstermek veya gizlemek istediğiniz sütunları seçin.  
  
#### <a name="to-change-the-order-of-the-columns"></a>Sütunların sırasını değiştirmek için  
  
-   Herhangi bir sütun başlığını istediğiniz konuma sürükleyin.  
  
##  <a name="userTasks"></a> Kullanıcı görevleri  
 Visual Studio 2015'te kullanıcı görev özelliği kaldırıldı. Ne zaman Visual Studio 2013'ten kullanıcı görev verileri olan bir çözümü açın ve daha önce Visual Studio 2015'te .suo dosyanızdaki kullanıcı görev verileri etkilenmez, ancak kullanıcı görevleri görev listesinde görüntülenmez.  
  
 Kullanıcı görev verilerinizi erişebilir ve devam etmek istiyorsanız, Visual Studio 2013'te projeyi açmak ve tercih edilen bir proje yönetim aracınızın (örneğin, Team Foundation Server) herhangi bir kullanıcı görevini içeriğini kopyalayın gerekir.  
  
##  <a name="tokensComments"></a> Belirteçler ve açıklamalar  
 Bir açıklamayı kodunuza açıklama işaretleyicisi ve önceden tanımlı belirteç tarafından öncesinde de görünür **görev listesi** penceresi. Örneğin, aşağıdaki C# açıklamasının üç ayrı bölümü vardır:  
  
-   Açıklama işaretleyicisi (`//`)  
  
-   Örneğin, belirteci (`TODO`)  
  
-   Açıklama (metnin geri kalanı)  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 Çünkü `TODO` önceden tanımlanmış olan olarak belirteç, bu yorumun görünür bir `TODO` listesinde görev.  
  
###  <a name="customTokens"></a> Özel belirteçler  
 Varsayılan olarak, Visual Studio aşağıdaki belirteçleri içerir: HACK, TODO, UNDONE, unutmayın. Bunlar büyük/küçük harfe duyarlı değildir.  
  
 Ayrıca kendi özel belirteçlerinizi de oluşturabilirsiniz.  
  
##### <a name="to-create-a-custom-token"></a>Özel bir belirteç oluşturmak için  
  
1.  Üzerinde **Araçları** menüsünde seçin **seçenekleri**.  
  
2.  Açık **ortam** klasörünü ve ardından **görev listesi**.  
  
     [Görev listesi, ortam, Seçenekler iletişim kutusu](../ide/reference/task-list-environment-options-dialog-box.md) görüntülenir.  
  
     ![Visual Studio görev listesi](../ide/media/vs2015-task-list-options.png "vs2015_task_list_options")  
  
3.  İçinde **belirteçleri** kategori içinde **adı** metin kutusuna belirtecinizin adını girin, örneğin "hata".  
  
4.  İçinde **öncelik** aşağı açılan listesinde, yeni belirteç için varsayılan bir öncelik seçin. Seçin **Ekle** düğmesi.  
  
###  <a name="cppComments"></a> C++ TODO açıklamaları  
 C++ TODO açıklamaları görüntülenen varsayılan olarak, **görev listesi** penceresi. Bu davranışı değiştirebilirsiniz.  
  
##### <a name="to-turn-off-c-todo-comments"></a>Devre dışı bırakmak için C++ TODO yorumları.  
  
1.  Üzerinde **Araçları** menü, Git **seçenekleri &#124; metin düzenleyici &#124; C/C++ &#124; görünümü &#124; açıklama görevlerini numaralandır** ve değeri false olarak ayarlayın.  
  
2.  İçinde **seçenekleri** açık iletişim kutusunu **metin düzenleyici**.  
  
3.  Altında **C/C++**, seçin **görünümü**ve ardından **açıklama görevlerini numaralandır** için **False**.  
  
##  <a name="shortcuts"></a> Kısayolları  
 A *kısayol* izleneceğini kodda bir yer işareti **görev listesi**; normal bir yer işareti daha farklı bir simgesi vardır. Kısayoluna çift **görev listesi** kod içinde ilgili konuma gitmek için.  
  
 ![Visual Studio görev listesi kısayolu simgesi](../ide/media/vs2015-task-list-bookmark.png "vs2015_task_list_bookmark")  
  
#### <a name="to-create-a-shortcut"></a>Bir kısayol oluşturmak için  
  
-   İşaretçiyi, kod içinde kısayolu yerleştirmek istediğiniz yere ekleyin. Seçin **Düzenle &#124; yer işaretleri &#124; görev listesi kısayolu Ekle** veya basın (klavye: Ctrl + K, Ctrl + H).  
  
     Kod içindeki kısayollar arasında gezinmek için listeden bir kısayol seçin ve ardından **sonraki görev** veya **önceki görev** kısayol menüsünden.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Listesi, Ortam, Seçenekler İletişim Kutusu](../ide/reference/task-list-environment-options-dialog-box.md)



