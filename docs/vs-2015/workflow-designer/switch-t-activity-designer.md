---
title: Anahtar&lt;T&gt; etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 01e583db3bb5b5aff6608b4028636823b4ca857c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844715"
---
# <a name="switchlttgt-activity-designer"></a>Anahtar&lt;T&gt; etkinlik Tasarımcısı
<xref:System.Activities.Statements.Switch%601> Etkinlik belirtilen ifadeyi hesaplar ve ilişkili anahtarı değerlendirmesinden gelen alınan değer eşleşen etkinlikler koleksiyonundan bir etkinliği yürütür.  
  
 **Anahtar\<T >** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.Switch%601> etkinliğinde [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
## <a name="the-switchtactivity"></a>Anahtar\<T > etkinliği  
 A <xref:System.Activities.Statements.Switch%601> etkinliği içeren bir <xref:System.Activities.Statements.Switch%601.Expression%2A> ve bir sözlükten <xref:System.Activities.Statements.Switch%601.Cases%2A>. Her durumda sözlük içeren bir çiftinden oluşur. bir *anahtarı* ve kendi ilişkili olarak hizmet veren bir etkinlik *değer*. <xref:System.Activities.Statements.Switch%601> Etkinlik değerlendirir <xref:System.Activities.Statements.Switch%601.Expression%2A> ve her bir anahtarı karşı karşılaştırır. Bir eşleşme bulunursa buna karşılık gelen etkinlik yürütülür. Sözlük anahtarları sözlüğün eşitliği karşılaştırıcısı tarafından tanımlanan eşitlik türüne göre benzersiz olması gerektiğinden, yalnızca bir eşleşme mümkündür. Eşleşme bulunursa <xref:System.Activities.Statements.Switch%601.Default%2A> etkinlik yürütülür.  
  
## <a name="how-to-use-the-switcht-activity-designer"></a>Anahtar kullanacak şekilde nasıl\<T > etkinlik Tasarımcısı  
 **Anahtar\<T >** etkinlik Tasarımcısı bulunabilir **akış denetimi** kategorisi **araç kutusu**, hangi erişilen tıklayarak**Araç kutusu** sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünü veya CTRL + ALT + X.) İçine bırakmadan sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)], görüntülediği **türleri seçin** genel tür belirtmesine izin vermek için iletişim *T* kullanılan <xref:System.Activities.Statements.Switch%601> etkinlik. Varsayılan değer **Int32**. Bir kez genel tür *T* seçilmedi, bir **anahtar\<T >** Tasarımcısı, iş akışı Tasarımcısı eklenir.  
  
 Şunlardır özelliklerini **anahtar\<T >** Tasarımcısı. Bu özelliklerin tümünü özellik kılavuzunda düzenlenebilir. Bunlardan bazıları da tasarımcı yüzeyinde düzenlenebilir.  
  
 Aşağıdaki tabloda en kullanışlı gösterilmektedir <xref:System.Activities.Statements.Switch%601> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı belirtir <xref:System.Activities.Statements.Switch%601> etkinlik Tasarımcısı. Varsayılan değer anahtarıdır\<Int32 >. Değer içinde düzenlenebilir **özellikleri** penceresi veya doğrudan Tasarımcı başlığı.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Doğru|Bu durumda, yürütülecek belirlemek için çalışmaları koleksiyondaki anahtarların ile karşılaştırmak için kullanılan ifade belirtir.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Eşleşme bulunursa çalıştırılan etkinlik belirtir. Tıklayın **etkinlik Ekle** açmak için tasarımcıda düğmesinde **varsayılan** burada etkinlik bırakılan kutusunu.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Değerlendirilecek çalışmaları belirtir. Bir durum eklemek için tıklatın **yeni servis talebi Ekle** düğme alttaki **anahtar\<T >** Tasarımcısı. Düğme TextBox'a değiştirir (genel tür anahtarı eklerken seçtiyseniz, birleşik giriş kutusu\<T > dize veya sabit listesi). Bir anahtar olarak ekledikten sonra **Case değeri** kutusunda büyük/küçük harf alanı genişler ve bir etkinlik bırakılabilir burada çalışması için yürütme mantığı tanımlamak için ipucu metnini "Buraya Bırak etkinlik".|  
  
 Büyük/küçük harf anahtarları yinelenmemesini sürece birden çok durum eklenebilir. Aksi takdirde bir hata iletişim kutusu belirtilen büyük/küçük harf anahtar zaten raporlama ve farklı bir anahtar seçmelisiniz görüntüler. İçinde **anahtar\<T >** yalnızca bir servis talebi alan Genişletilmiş görünümde bir zaman Tasarımcısı olabilir. Büyük/küçük harf alan daraltılmış Görünümü'nde ise, büyük/küçük alana tıklayarak genişlediğinden genişler. Daraltılmış bir servis talebi için tasarımcı etkinlik çalışması içinde görünen adını sağ tarafta olup olmadığını herhangi gösterdiğine dikkat edin. Aksi halde gösteren **etkinlik Ekle** tıklatarak durum genişler ve bir etkinlik eklemenize olanak sağlayan düğme.  
  
 Case anahtar düzenleyebilmesi anahtarı mevcut çalışmasının tıklayarak anahtarı bir etiketten bir TextBox'a değiştirir.  
  
 Servis talebi silmek için 2 yolu vardır:  
  
1. Select case ve silin.  
  
2. Seçin bağlam menüsünü görüntülemek ve seçmek için büyük/küçük harf, sağ tıklatın **Sil**.  
  
   Durumun kendisini silmek için seçmelisiniz unutmayın. Seçme ve etkinliği bir durum içinde silme yalnızca durum etkinlik siler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)