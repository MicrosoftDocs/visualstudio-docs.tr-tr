---
title: 'Nasıl yapılır: projenizdeki yerel veri dosyalarını yönetme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 16e2d38dda97bd8a7f130254b2f23be9f17e0ac4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271381"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>Nasıl yapılır: Projenizdeki Yerel Veri Dosyalarını Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerel veritabanı dosyası bir proje dosyası olarak dahil edilebilir. Bir yerel veritabanı dosyasına ilk bağladığınızda projenizde bir kopyasını oluşturmak veya geçerli konumdaki varolan dosyaya bağlanmak seçebilirsiniz. Varolan dosyaya bağlarsanız, özgün konumunda bırakılır. Dosyayı projenize kopyalamak isterseniz, Visual Studio bir kopyasını oluşturur, projenize ekler ve bağlantıyı Kopyala işaret edecek şekilde değiştirir. Sunucu Gezgini'nde olanlar gibi diğer bağlantılar da değiştirilmiştir.  
  
 Özelliğinin varsayılan ayarı, kullanmakta olduğunuz veritabanı dosyasının türüne bağlıdır. Davranışını **çıkış dizinine Kopyala** özelliği Web veya C++ projeleri için geçerli değildir.  
  
 Geliştirme sırasında bu değişiklikleri kalıcı hale getirme olmadan kodunuzu etkilerini veritabanını görüntülemek isteyebilirsiniz. Bu ayarı tarafından yapabileceğiniz **çıkış dizinine Kopyala** özelliği true. Proje yapılarında veya F5 tuşuna basın. her zaman dosyanın bin klasörüne erişmeye kopyalanır ve bu dosyayı projenizin kök klasörüne bir dosya için değişiklik. Kök proje klasörünüzdeki veritabanı dosyası yalnızca, veritabanı şemasını veya verileri kullanarak düzenlediğinizde değiştirilir **Sunucu Gezgini**, **veritabanı Gezgini** veya diğer araç penceresi.  
  
 Aşağıdaki tabloda ayarları açıklanmaktadır **çıkış dizinine Kopyala** özelliği.  
  
|Ayar|Davranış|  
|-------------|--------------|  
|**Yeniyse Kopyala** (.sdf dosyaları için varsayılan)|Veritabanı dosyası proje dizinine kopyalanır **bin** ilk zaman Proje oluşturulur. Proje derleme sonraki her seferinde **değiştirme tarihi** dosyaları özelliği karşılaştırılır. Proje klasöründeki dosya daha yeniyse kopyalanır **bin** klasörü, oradaki geçerli dosyanın yerini alır. Varsa dosyasında **bin** klasör yeniyse, hiçbir dosya kopyalanmaz. Bu ayar, uygulamanızı çalıştırın ve verilerde yapılan değişiklikleri kaydetmek her zaman, bu değişiklikler uygulamanızı bir sonraki çalıştırmanızda görünür olduğunu, yani çalışma zamanı sırasında verilerde yapılan değişiklikleri devam ettirir. **Dikkat:** bu seçeneği .mdb veya .mdf dosyaları için önermemekteyiz. Bile verilere herhangi bir değişiklik yapıldığında, veritabanı dosyası değişebilir. Yalnızca bir veri dosyasında bir bağlantı açmak (genişleterek gibi **tabloları** düğümünde **Sunucu Gezgini**) yeni olarak işaretleyebilir.|  
|**Her zaman Kopyala** (.mdf ve .mdb dosyaları için varsayılan)|Veritabanı dosyası, uygulamanızı her zaman proje dizininden / bin dizinine kopyalanır. Bu nedenle, uygulamanızı ve dosyanın/Bin dizinindeki değişiklikleri kaydedin, bu değişiklikleri özgün dosyanın / bin dizinine kopyalanır bir sonraki açışınızda üzerine yazılır.|  
|**Kopyalamayın**|Dosya hiçbir zaman kopyaladığınız veya proje sistemi tarafından üzerine. Bu ayarı kullanıyorsanız, el ile dosyayı proje dizininden çıktı dizinine kopyalamanız gerekir.|  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>Yerel veritabanı dosyası iletişim kutusuna yanıt vermek için  
  
-   Tıklayın **Evet** veritabanı dosyasını projenize kopyalamasını ve projenizdeki kopyaya bağlantıyı değiştirmek için Visual Studio istiyorsanız. Projenizdeki veritabanı dosyaları ile çalışma hakkında daha fazla bilgi için bkz. [Local Data Overview](../data-tools/local-data-overview.md).  
  
-   Tıklayın **Hayır** Visual Studio'nun veritabanı dosyasını projenize kopyalamasını istemiyorsanız. Bunun yerine, bağlantı noktaları dosyayı özgün konuma ve veritabanı dosyasına eklenmez bir dosya olarak projeye.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: bir yerel veritabanı dosyası (Windows Forms) verilere bağlanma](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Bir Access veritabanındaki verilere bağlanma (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)