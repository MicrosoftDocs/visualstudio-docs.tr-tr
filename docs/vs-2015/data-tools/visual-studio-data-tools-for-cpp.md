---
title: C++ için Visual Studio veri araçları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 030e142911078aec36b01335c8fb3aaa4d82ac78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849651"
---
# <a name="visual-studio-data-tools-for-c"></a>C++ için Visual Studio veri araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Veri kaynaklarına erişirken yerel C++ genellikle en hızlı performans sağlar. Ancak, veri Visual Studio'da C++ uygulamaları için Araçlar, .NET uygulamaları için olduğu gibi zengin değil. Örneğin, veri kaynaklarını windows sürükle ve bırak C++ tasarım yüzeyine veri kaynakları için kullanılamaz. Bir nesne ilişkisel katmanı gerekiyorsa, kendi yazmak veya bir üçüncü taraf ürün kullanım gerekecektir.  Microsoft Foundation Class kitaplığını kullanan uygulamaları bellekte veri depolamak ve kullanıcıya göstermek için belgeler ve görünümler, birlikte bazı veritabanı sınıfları kullanabilirsiniz, ancak aynı veri bağlama işlevselliği için geçerlidir. Daha fazla bilgi için [Visual C++'da veri erişimi](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .  
  
 SQL veritabanlarına bağlanmak için yerel C++ uygulamaları, ODBC ve OLE DB sürücüleri ve Windows ile birlikte ADO sağlayıcıyı kullanabilirsiniz.     Bunlar, bu arabirimleri destekleyen herhangi bir veritabanına bağlanabilirsiniz. ODBC sürücüsü standardıdır. OLE DB, geriye dönük uyumluluk için sağlanır. Bu veri teknolojileri hakkında daha fazla bilgi için bkz. [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 SQL Server 2005'te özel işlevsellikten yararlanmak ve daha sonra kullanmak üzere [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Yerel istemci ayrıca SQL Server ODBC sürücüsünü ve SQL Server OLE DB sağlayıcısı bir yerel dinamik bağlantı kitaplığı (DLL) içerir. Bu, Microsoft SQL Server için yerel kodlu API'ler (ODBC, OLE DB ve ADO) kullanan uygulamaları destekler.  SQL Server veri araçları ile SQL Server Native Client yükler. Programlama Kılavuzu aşağıda verilmiştir: [SQL Server yerel istemcisi programlama](https://msdn.microsoft.com/library/ms130892.aspx).  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Bir C++ uygulamasından localDB ODBC ve SQL Native Client aracılığıyla bağlanmak için  
  
1. SQL Server veri Araçları'nı yükleyin.  
  
2. Örnek SQL veritabanına bağlanmak için gerekiyorsa, Northwind veritabanı indirin ve yeni bir konuma sıkıştırmasını açın.  
  
3. LocalDB sıkıştırması Northwind.mdf dosya eklemek için SQL Server Management Studio'yu kullanın. SQL Server Management Studio başlatıldığında (localdb) \MSSQLLocalDB bağlanın.  
  
    ![SSMS bağlanma iletişim](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS bağlanma iletişim kutusu")  
  
    Ardından localdb düğümü sol bölmede sağ tıklatın ve seçin **iliştirme**.  
  
    ![Veritabanını SSMS ekleme](../data-tools/media/raddata-ssms-attach-database.png "raddata veritabanını SSMS ekleme")  
  
4. ODBC Windows SDK örneği indirin ve yeni bir konuma sıkıştırmasını açın. Bu örnek, bir veritabanı ve çıkış sorguları ve komutları bağlanmak için kullanılan temel ODBC komutları gösterir. Bu işlevler hakkında daha fazla bilgi [Microsoft açık veritabanı bağlantısı (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). (Bu, C++ klasöründe bulunur) çözümü ilk kez yüklediğinizde, Visual Studio çözümü Visual Studio'nun geçerli sürümüne yükseltme olanağı sunar. **Evet**'i tıklayın.  
  
5. Yerel istemci kullanmak için lib dosya ve üstbilgi dosyası gerekir. Bu dosyalar, İşlevler ve sql.h içinde tanımlanan ODBC işlevleri ötesinde SQL Server'a özel tanımları içerir. İçinde **proje** > **özellikleri** > **VC ++ dizinleri**, aşağıdakileri içeren dizin ekleyin:  
  
   **\<Sistem sürücüsü >: \Program SQL Server\110\SDK\Include** ve bu kitaplık dizini:  
  
   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6. Odbcsql.cpp içinde şu satırı ekleyin. #Define ilgisiz OLE DB tanımları derlenen engeller.  
  
   ```  
   #define _SQLNCLI_ODBC_  
   #include <sqlncli.h>  
   ```  
  
    Önceki adımlarda, derlemek ve çalıştırmak için gerekli değildir. Bu nedenle örnek gerçekten yerel istemci işlevleri kullanımda bulunmadığını unutmayın. Ancak, proje artık bu işlevselliği kullanmak için yapılandırılır. Daha fazla bilgi için [SQL Server yerel istemcisi programlama](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).  
  
7. ODBC alt sistemi kullanmak üzere hangi sürücüyü belirtin. Örnek sürücü bağlantı dizesi özniteliği, bir komut satırı bağımsız değişkeni geçirir. İçinde **proje** > **özellikleri** > **hata ayıklama**, bu komut bağımsız değişkeni ekleyin:  
  
   ```  
   DRIVER="SQL Server Native Client 11.0"  
   ```  
  
8. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Sürücüsünden bir veritabanı girmenizi isteyen bir iletişim kutusu görmeniz gerekir. Girin `(localdb)\MSSQLLocalDB`ve **güvenilir bağlantı kullan**. Tuşuna **Tamam**. Başarılı bir bağlantı iletileri konsoluyla görmeniz gerekir. Ayrıca SQL deyiminde girebileceğiniz bir komut istemini görmeniz gerekir. Aşağıdaki ekranda bir örnek sorgu ve sonuçları gösterir:  
  
    ![ODBC örnek sorgu çıktısı](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC örnek sorgu çıktısı")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)


