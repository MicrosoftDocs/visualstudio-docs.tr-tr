---
title: Python Django web projesi şablonu
description: Visual Studio ile Python Django web uygulamalarını hızlı oluşturulması için kapsamlı bir şablon sağlayın.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c1aba68ad8cde6aebbc881e61937dc53037b58c5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066528"
---
# <a name="django-web-project-template"></a>Django web projesi şablonu

[Django](https://www.djangoproject.com/) , hızlı, güvenli ve ölçeklenebilir bir web geliştirme için tasarlanan yüksek düzeyli bir Python altyapısıdır. Visual Studio'da Python desteği, yapıyı bir Django tabanlı bir web uygulamasının ayarlamak için birçok proje şablonları sağlar. Visual Studio'da bir şablon kullanmak için **dosya** > **yeni** > **proje**"Django" için arama yapın ve listeden  **Django Web projesi boş**, **Django Web projesi**, ve **yoklamalar Django Web projesi** şablonları. Bkz: [öğrenin Django öğretici](learn-django-in-visual-studio-step-01-project-and-solution.md) tüm şablonları kılavuz.

Visual Studio, Django projeleri için IntelliSense sağlar:

- Bağlam değişkenleri şablona geçirildi:

    ![Bağlam değişkenleri için IntelliSense](media/template-django-intellisense.png)

- Etiketleme ve için hem yerleşik olanları filtreleme ve kullanıcı tanımlı:

    ![Etiketleri ve filtreler için IntelliSense](media/template-django-intellisense-filter.png)

- Sözdizimi: Katıştırılmış CSS ve JavaScript için renklendirme

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio ayrıca sağlar tam [hata ayıklama desteği](debugging-python-in-visual-studio.md) Django projeleri için: 

![Kesme noktaları](media/template-django-debugging.png)

Django projelerin aracılığıyla yönetilen tipik kendi *manage.py* dosyasını Visual Studio izlediği varsayılır. Giriş noktası olarak bu dosyayı kullanarak durdurursanız, proje dosyası temelde bölün. Bu durumda için ihtiyacınız [projeden varolan dosyaları yeniden](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) olmadan bir Django projesi olarak işaretleniyor.

## <a name="django-management-console"></a>Django Yönetim Konsolu

Django Yönetim Konsolu çeşitli komutlara üzerinden erişilen **proje** menüsü veya projeye sağ tıklayarak **Çözüm Gezgini**.

- **Django Kabuğu'nu açın**: uygulama Bağlamınızı Modellerinizi yönetmenize olanak sağlayan bir kabuk açılır:

    ![Açık Django Kabuk komutu sonuçları](media/template-django-console-shell.png)

- **Django eşitleme DB**: yürütür `manage.py syncdb` içinde bir **etkileşimli** penceresi:

    ![Django eşitleme DB komutunun sonucu](media/template-django-console-sync-db.png)

- **Statik toplamak**: yürütür `manage.py collectstatic --noinput` tarafından belirtilen yol için tüm statik dosyaları kopyalamak için `STATIC_ROOT` içinde *settings.py*.

    ![Toplama statik komutunun sonucu](media/template-django-console-collect-static.png)

- **Doğrulama**: yürütür `manage.py validate`, hangi raporların tarafından belirtilen yüklü modellerindeki herhangi bir doğrulama hatası `INSTALLED_APPS` içinde *settings.py*:

    ![Doğrulama komutunun sonucu](media/template-django-console-validate.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Django öğretici öğrenin](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
