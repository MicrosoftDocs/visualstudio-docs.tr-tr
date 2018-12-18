---
title: 'Nasıl yapılır: gölgelendiriciyi dışarı aktarma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8c3a6ea90b43caeb1140cbb9ab7c699bdb09c3e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213297"
---
# <a name="how-to-export-a-shader"></a>Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede, böylece uygulamanızda kullanabilirsiniz yönlendirilmiş grafik gölgelendirici dili (DGSL) gölgelendiriciyi dışarı aktarma için gölgelendirici Tasarımcısı'nı nasıl yapılacağı açıklanır.  
  
 Bu belge, bu etkinlik gösterir:  
  
-   Gölgelendiriciyi dışarı aktarma  
  
## <a name="exporting-a-shader"></a>Gölgelendiriciyi dışarı aktarma  
 Gölgelendirici Tasarımcısı'nı kullanarak ve uygulamanızda kullanmadan önce bir gölgelendirici oluşturduktan sonra bunu, grafik API'si anlayan bir biçimde dışarı aktarmanız gerekir. Farklı ihtiyaçları karşılamak üzere farklı şekillerde gölgelendiriciyi dışarı aktarabilirsiniz.  
  
#### <a name="to-export-a-shader"></a>Gölgelendiriciyi dışarı aktarmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], açık bir **görsel gölgelendirici grafiği (.dgsl)** dosya.  
  
     Yoksa bir **görsel gölgelendirici grafiği (.dgsl)** açın, içinde açıklandığı gibi oluşturmak için dosya [nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Üzerinde **gölgelendirici Tasarımcısı** araç seçin **Gelişmiş**, **dışarı**, **dışarı aktarma olarak**. **Gölgelendiriciyi dışarı aktarma** iletişim kutusu görüntülenir.  
  
3.  İçinde **farklı kaydetme türü** aşağı açılan listesinde, dışa aktarmak istediğiniz biçimi seçin.  
  
     Seçebileceğiniz biçimler şunlardır:  
  
     **HLSL piksel gölgelendiricisi (\*.hlsl)**  
     Gölgelendirici üst düzey gölgelendirici dili (HLSL) kaynak kodu dışarı aktarır. Bu seçenek, bir uygulamada bile dağıtıldıktan sonra gölgelendirici daha sonra değiştirmek mümkün kılar. Bu, hata ayıklama ve son kullanıcı sorunları göre kod düzeltme eki kolaylaştırabilir, ancak aynı zamanda istenmeyen yollarla gölgelendiricinize değiştirmek bir kullanıcı için kolaylaştırır — Örneğin, bir rekabet oyununda bir haksız avantaj elde etmek için. Gölgelendirici yükleme süresi da artırabilir.  
  
     **Derlenmiş piksel gölgelendiricisi (\*.cso)**  
     Gölgelendirici HLSL bayt dışarı aktarır. Bu seçenek gölgelendirici daha sonra bir uygulamada bile dağıtıldıktan sonra değiştirmek mümkün hale getirir. Bu, hata ayıklama ve son kullanıcı sorunları göre kod düzeltme eki kolaylaştırabilir, ancak önceden derlenmiş gölgelendirici olduğundan, gölgelendirici uygulama tarafından yüklendiğinde, ek çalışma zamanı yükü tabi değildir. Yeterince deneyimli kullanıcılar hala istenmeyen yollarla gölgelendiriciyi değiştirebilirsiniz, ancak gölgelendirici derleme bu önemli ölçüde daha zor hale getirir.  
  
     **C++ üst bilgisi (\*.h)**  
     Gölgelendirici HLSL bayt içeren bir bayt dizisi tanımlayan bir C stili başlığı dışarı aktarır. Bu seçenek, hata ayıklama ve son kullanıcı sorunlarını düzeltme test etmek için uygulamayı yeniden derlenmesi için temel kod düzeltme eki daha fazla zaman zorlaştırabilir. Ancak, bu seçenek, imkansız olsa, bir uygulama dağıtıldıktan sonra gölgelendirici değiştirmek zorlaştırır çünkü gölgelendirici istenmeyen yollarla değiştirmek isteyen bir kullanıcı için birçok zorluk sunduğu.  
  
4.  İçinde **dosya adı** birleşik giriş kutusu, dışarı aktarılan gölgelendirici için bir ad belirtin ve ardından **Kaydet** düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md)   
 [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)



