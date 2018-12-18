---
title: 'Nasıl Yapılır: Bağlantı Dizelerini Kaydetme ve Düzenleme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 050d5f7bcda86890642a5bef10fa04d2c12b4203
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089237"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Nasıl yapılır: kaydetme ve bağlantı dizeleri düzenleme
Visual Studio uygulama bağlantı dizeleri (uygulama ayarları da bilinir) uygulama yapılandırma dosyasında kaydedilen veya doğrudan uygulamanızda sabit kodlanmış. Uygulama yapılandırma dosyasında bağlantı dizelerini kaydetme uygulamanızı sürdürme görevini basitleştirir. Bağlantı dizesi değiştirilmesi gerekiyorsa, (kaynak kodunda değiştirin ve uygulamayı yeniden derlemenize gerek kalmadan) aksine uygulama ayarları dosyasında güncelleştirebilirsiniz.

Bağlantı dizesi içinde (örneğin, parola) hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Uygulama yapılandırma dosyasına kaydedilen bağlantı dizeleri şifrelenmez veya gizlenmiş birisi için dosyaya erişmek ve içeriğini görüntülemek mümkün olabilir. Windows tümleşik güvenliği kullanarak, bir veritabanına erişimi denetlemek için daha güvenli bir yoludur.

Kullanmayı seçmezseniz Windows tümleşik güvenlik ve veritabanınızı bir kullanıcı adı ve parola gerektirir, bağlantı dizesinden atlayabilirsiniz ancak uygulamanız başarıyla veritabanına bağlanmak için bu bilgiyi sağlamanız gerekir. Örneğin, bağlantı dizesi çalışma zamanında dinamik olarak oluşturur ve bu bilgileri kullanıcıya sorar bir iletişim kutusu oluşturabilirsiniz. Bilgileri veritabanına şekilde yakalanırsa güvenlik hala bir sorun olabilir.
Daha fazla bilgi için bkz: [bağlantı bilgileri koruma](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Veri Kaynağı Yapılandırma Sihirbazı'nı içinde bir bağlantı dizesi kaydetmek için
İçinde **veri kaynağı Yapılandırma Sihirbazı**, bağlantıyı kaydetmek için seçeneğini **bağlantı dizesini uygulama yapılandırma dosyasını Kaydet** sayfa.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Bir bağlantı dizesi doğrudan uygulama ayarlarını kaydetmek için
1. İçinde **Çözüm Gezgini**, çift **My proje** simgesi (Visual Basic) veya **özellikleri** simgesi (açmak için C#) **Proje Tasarımcısı** .
1. Seçin **ayarları** sekmesi.
1. Girin bir **adı** bağlantı dizesi. Bu ad, kodu bağlantı dizesinde erişirken bakın.
1. Ayarlama **türü** için (**bağlantı dizesi**).
1. Bırakın **kapsam** kümesine **uygulama**.
1. Bağlantı dizenizi yazın **değeri** tıklayın veya alanı **üç nokta** (...) düğmesini **değeri** açmak için alanını **bağlantı özelliklerini** , bağlantı dizesi oluşturma iletişim kutusu.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Uygulama ayarları depolanan bağlantı dizeleri düzenleme
Uygulama ayarları kullanılarak kaydedilmiş bağlantı bilgilerini değiştirebileceğiniz **Proje Tasarımcısı**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Uygulama ayarları depolanan bağlantı dizesini düzenlemek için
1. İçinde **Çözüm Gezgini**, çift **My proje** simgesi (Visual Basic) veya **özellikleri** simgesi (açmak için C#) **Proje Tasarımcısı** .
1. Seçin **ayarları** sekmesi.
1. Bulmak istediğiniz metni seçin ve düzenlemek için bağlantı **değeri** alan.
1. Bağlantı dizesinde Düzenle **değeri** tıklayın veya alanı **üç nokta** (...) düğmesini **değeri** bağlantınızla düzenlemek için alan **bağlantı Özellikler** iletişim kutusu.

## <a name="edit-connection-strings-for-datasets"></a>Veri kümeleri için bağlantı dizelerini Düzenle
Bir veri kümesinde her TableAdapter bağlantı bilgilerini değiştirebilirsiniz.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Bir TableAdapter içinde bir veri kümesi için bir bağlantı dizesini düzenlemek için
1. İçinde **Çözüm Gezgini**, veri kümesine çift tıklayın (**.xsd** dosyası) düzenlemek istediğiniz bağlantı vardır.
1. Seçin **TableAdapter** veya düzenlemek istediğiniz bağlantıya sahip sorgu.
1. İçinde **özellikleri** penceresinde genişletin **bağlantı düğümü**.
1. Hızlı bir şekilde bağlantı dizesini değiştirmek için Düzenle **ConnectionString** özelliği veya aşağı oka tıklayın **bağlantı** özelliği ve **yeni bağlantı**.

## <a name="security"></a>Güvenlik
Bağlantı dizesi içinde (örneğin, parola) hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows tümleşik güvenliği kullanarak, bir veritabanına erişimi denetlemek için daha güvenli bir yoludur.
Daha fazla bilgi için bkz: [bağlantı bilgileri koruma](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları ekleme](../data-tools/add-new-connections.md)