---
title: Özel yerel ETW yığın olayları | Microsoft Docs
ms.custom: ''
ms.date: 02/24/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 98fc473a9459aa6d1a1d7c10be7b6f240a4ab7d0
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744996"
---
# <a name="custom-native-etw-heap-events"></a>Özel yerel ETW yığın olayları

Visual Studio içeren çeşitli [profil oluşturma ve tanılama araçları](../profiling/profiling-feature-tour.md), bir yerel bellek profili Oluşturucu dahil olmak üzere.  Bu profil oluşturucu kancaları [ETW olayları](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) yığın sağlayıcısından ve bellek nasıl yapılıyor, analizini sağlar ayrılmış ve kullanılan.  Varsayılan olarak, bu araç yalnızca standart Windows yığından yapılan ayırmaların çözümleyebilir ve bu yerel yığın dışında herhangi bir ayırma değil görüntülenir.

Çoğu durumda, kendi özel yığının kullanın ve ayırma ek standart yığın yükünden kaçınmak isteyebilirsiniz vardır.  Örneğin, kullanabilirsiniz [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) büyük miktarda bellek oyun ve uygulama başlangıcında ayırmak ve sonra bu listeyi kendi taşlarına yönetin.  Bu senaryoda, bellek profili Oluşturucu aracı yalnızca bu ilk ayırma ve bellek öbeği içinde yapılan değil özel yönetim görür.  Ancak, özel yerel yığın ETW Sağlayıcısı'nı kullanarak, standart yığın dışında yaptığınız herhangi bir ayırma hakkında bilmeniz aracı sağlayabilirsiniz.

Örneğin, aşağıdaki gibi bir projedeki burada `MemoryPool` özel bir yığın Windows yığında yalnızca tek bir ayırma görür:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes 
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Anlık görüntüden [bellek kullanımı](../profiling/memory-usage.md) izleme özel yığının yalnızca tek 8192 bayt ayırma ve havuz tarafından yapılan özel ayrımlara hiçbiri gösterebilir olmadan aracı:

![Windows yığın ayırma](media/heap-example-windows-heap.png)

Aşağıdaki adımları gerçekleştirerek, biz özel bizim yığında bellek usgae izlemek için aynı bu aracı kullanabilirsiniz.

## <a name="how-to-use"></a>Kullanma

Bu kitaplık, C ve C++ içinde kolayca kullanılabilir.

1. Üst bilgisi için özel yığının ETW sağlayıcısı ekleyin:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Ekleme `__declspec(allocator)` dekoratör için herhangi bir işlevde özel yığının yöneticinize yeni ayrılan yığın bellek için bir işaretçi döndürür.  Bu dekoratör doğru iade edilen bellek türünü tanımlamak için aracı sağlar.  Örneğin:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```
   
   > [!NOTE]
   > Bu dekoratör derleyici, bu işlev çağrısı bir ayırıcı olduğunu bildirir.  Her işlev çağrısı çıkarır çağıran site adresini, çağrı talimatı boyutunu ve yeni bir yeni nesne typeid'ye `S_HEAPALLOCSITE` simgesi.  Bir çağrı yığını atandığında, bu bilgileri içeren bir ETW olay Windows yayar.  Bellek profili Oluşturucu aracı dönüş adresi eşleştirme için arama çağrı yığını size yol gösterir. bir `S_HEAPALLOCSITE` sembol ve simge TypeID bilgileri ayırma çalışma zamanı türünü görüntülemek için kullanılır.
   >
   > Şuna benzer bir çağrı kısa, yani `(B*)(A*)MyMalloc(sizeof(B))` araç türü olarak görünecek `B`değil `void` veya `A`.

1. C++ için oluşturma `VSHeapTracker::CHeapTracker` profil oluşturma Aracı'nda görünür öbek için bir ad sağlayarak, nesne:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   C kullanıyorsanız `OpenHeapTracker` işlevini.  Bu işlev, diğer izleme işlevlerini çağırırken kullanacağınız bir tanıtıcı döndürür:
  
   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Özel işlevinizi kullanarak bellek ayırırken çağrı `AllocateEvent` (C++) veya `VSHeapTrackerAllocateEvent` işaretçinin bellek ve ayırma izlemek için boyutuna geçirme (C) yöntemi:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   veya

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Özel bellek ayırıcısı işlevinizi etiketi unutmayın `__declspec(allocator)` daha önce açıklanan dekoratör.

1. Özel işlevinizi kullanarak belleğini aramanızı `DeallocateEvent` (C++) veya `VSHeapTracerDeallocateEvent` bellek ayırmayı kaldırma izlemek için işaretçiyi geçirme (C) işlevi:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   veya:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Özel işlevinizi kullanarak bellek ayrılırken çağrı `ReallocateEvent` (C++) veya `VSHeapReallocateEvent` (C) yöntemi, bir işaretçi geçirerek yeni bellek, ayırma ve eski bellek işaretçi boyutu:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   veya:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Son olarak, kapatın ve c++ özel yığının İzleyici temizlemek için kullanın `CHeapTracker` yok Edicisi, elle veya standart ölçüm kuralları aracılığıyla veya `CloseHeapTracker` c: işlevi

   ```cpp
   delete pHeapTracker;
   ```

   veya:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Bellek kullanımı İzle
Bu çağrılar yerinde özel yığının kullanımınızı artık standardı kullanılarak izlenebilir **bellek kullanımı** Visual Studio'daki aracı.  Bu aracı kullanma hakkında daha fazla bilgi için lütfen bkz [bellek kullanımı](../profiling/memory-usage.md) belgeleri. Yığın profili oluşturmayı, görüntülenen özel yığının kullanımınızı görmeyeceğiniz anlık görüntüler sayesinde, aksi takdirde etkin olun. 

![Yığın profili oluşturmayı etkinleştir](media/heap-enable-heap.png)

İzleme, özel yığının görüntülemek için kullanın **yığın** açılan sağ üst köşesinde bulunan **anlık görüntü** görünümden değiştirmek için pencere *NT yığını* kendi yığına daha önce adı.

![Yığın seçimi](media/heap-example-custom-heap.png)

Yukarıdaki kod örneğinde ile `MemoryPool` oluşturma bir `VSHeapTracker::CHeapTracker` nesnesi ve kendi `allocate` artık çağırma yöntemi `AllocateEvent` yöntemi, artık görebilirsiniz, özel ayırma sonucu 24 bayt hepsini toplam üç örnek gösteriliyor tür `Foo`.

Varsayılan *NT yığını* yığın arar aynı daha önce ' nın eklenmesiyle bizim `CHeapTracker` nesne.

![NT yığını ile İzleyicisi](media/heap-example-windows-heap.png)

Standart Windows yığın ile bu aracı sızıntıları ve bozulma için ana açıklanan, özel yığının bakın ve anlık görüntüsünü karşılaştırmak için de kullanabilirsiniz gibi [bellek kullanımı](../profiling/memory-usage.md) belgeleri.

> [!TIP]
> Visual Studio da içeren bir **bellek kullanımı** aracına **performans profili oluşturma** etkinleştirildiğinden araç takımı **hata ayıklama**  >   **Performans Profiler** menü seçeneğini veya **Alt**+**F2** klavye birleşimi.  Bu özellik, yığın izleme içermez ve burada açıklandığı gibi özel yığının görüntülenmez.  Yalnızca **tanılama araçları** ile etkin hale getirilebilir penceresinde **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**  menüsünden veya **Ctrl**+**Alt**+**F2** klavye birleşimi, bu işlevler içerir.

## <a name="see-also"></a>Ayrıca bkz.
[Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)  
[Bellek Kullanımı](../profiling/memory-usage.md)
