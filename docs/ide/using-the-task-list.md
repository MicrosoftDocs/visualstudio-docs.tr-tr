---
title: Görev Listesini Kullanma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7766a7fd935cc1e1131c4780a5a88ef6fa54e838
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349406"
---
# <a name="use-the-task-list"></a>Görev Listesini Kullanma

Kullanma **görev listesi** gibi belirteçler kullanan kod açıklamaları izlemek için `TODO` ve `HACK`, ya da özel belirteçler ve önceden tanımlanmış bir kodun konumu için doğrudan kısayolları yönetmek için. Kaynak kodu konumuna gitmek için liste öğesine tıklayın.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Görev açıklamaları (Mac için Visual Studio)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Görev Listesi penceresi

Zaman **görev listesi** olan açık, uygulama penceresinin altında görünür.

Açmak için **görev listesi**seçin **görünümü** > **görev listesi**, veya klavye Press'ten **Ctrl** + **\\**,**T**.

![Görev Listesi penceresi](../ide/media/vs2015_task_list.png)

Listenin sıralama düzenini değiştirmek için herhangi bir sütun başlığını seçin. Arama sonuçlarınızı iyice daraltmak için basın **Shift** ve ikinci bir sütun başlığına tıklayın. Alternatif olarak, kısayol menüsünden seçin **sıralama ölçütü**, bir başlığı seçin. Arama sonuçlarınızı iyice daraltmak için basın **Shift** ve ikinci bir başlık seçin.

Kısayol menüsünde sütunları göster veya gizle tercih **sütunları göster**. Göstermek veya gizlemek istediğiniz sütunları seçin.

Sütunların sırasını değiştirmek için herhangi bir sütun başlığını istediğiniz konuma sürükleyin.

## <a name="user-tasks"></a>Kullanıcı görevleri

Visual Studio 2015'te kullanıcı görev özelliği kaldırıldı. Visual Studio 2013'ten ve daha önce kullanıcının Görev verileri içeren bir çözümü açtığınızda, kullanıcının Görev verileri, *.suo* dosya etkilenmez, ancak kullanıcı görevleri görev listesinde görüntülenmez.

Erişim ve kullanıcı görev verilerinizi güncelleştirme, Visual Studio 2013'te projeyi açmak ve tercih edilen bir proje yönetim aracınızın (örneğin, Team Foundation Server) herhangi bir kullanıcı görevini içeriğini kopyalayın devam etmek istiyorsanız.

## <a name="tokens-and-comments"></a>Belirteçler ve açıklamalar

Bir açıklamayı kodunuza açıklama işaretleyicisi ve önceden tanımlı belirteç tarafından öncesinde ayrıca şurada görünür **görev listesi**. Örneğin, aşağıdaki C# açıklamasının üç ayrı bölümü vardır:

- Açıklama işaretleyicisi (`//`)

- Örneğin, belirteci (`TODO`)

- Açıklama (metnin geri kalanı)

```csharp
// TODO: Load state from previously suspended application
```

Çünkü `TODO` önceden tanımlanmış olan olarak belirteç, bu yorumun görünür bir `TODO` listesinde görev.

### <a name="custom-tokens"></a>Özel belirteçler

Varsayılan olarak, Visual Studio aşağıdaki belirteçleri içerir: `HACK`, `TODO`, `UNDONE`, ve `UnresolvedMergeConflict`. Bunlar büyük küçük harfe duyarlı değildir. Ayrıca kendi özel belirteçlerinizi de oluşturabilirsiniz.

Özel bir belirteç oluşturmak için:

1. Üzerinde **Araçları** menüsünde seçin **seçenekleri**.

2. Açık **ortam** klasörünü ve ardından **görev listesi**.

   [Görev listesi seçenekleri sayfasında](../ide/reference/task-list-environment-options-dialog-box.md) görüntülenir.

   ![Visual Studio görev listesi](../ide/media/vs2015_task_list_options.png)

3. İçinde **adı** metin kutusunda, belirtecinizin adını girin, örneğin **hata**.

4. İçinde **öncelik** aşağı açılan listesinde, yeni belirteç için varsayılan bir öncelik seçin.

5. Seçin **ekleme**.

### <a name="c-todo-comments"></a>C++ TODO açıklamaları

C++ TODO açıklamaları görüntülenen varsayılan olarak, **görev listesi**.

C++ TODO yorumları kapattı devre dışı bırakmak için **Araçları** menüsünde seçin **seçenekleri** > **metin düzenleyici** > **C/C++**  >  **Görünümü** > **açıklama görevlerini numaralandır**ve değerine **false**.

## <a name="shortcuts"></a>Kısayollar

A *kısayol* izleneceğini kodda bir yer işareti **görev listesi**. Bu, normal bir yer işareti daha farklı bir simgesi vardır. Kısayoluna çift **görev listesi** kod içinde ilgili konuma gitmek için.

![Visual Studio görev listesi kısayolu simgesi](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Bir kısayol oluşturma

Bir kısayol oluşturmak için işaretçiyi kısayolu yerleştirmek istediğiniz kodu ekleyin. Seçin **Düzenle** > **yer işaretleri** > **görev listesi kısayolu Ekle** veya basın **Ctrl** + **K**, **Ctrl**+**H**.

Kod içindeki kısayollar arasında gezinmek için listeden bir kısayol seçin ve ardından **sonraki görev** veya **önceki görev** kısayol menüsünden.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev listesi, ortam, Seçenekler iletişim kutusu](../ide/reference/task-list-environment-options-dialog-box.md)
- [Görev açıklamalarını (Mac için Visual Studio)](/visualstudio/mac/task-comments)
