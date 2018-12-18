---
title: 'İzlenecek yol: LinqToXmlDataBinding örneği'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 824896a4e381a6a8d5c5e0935010b1cf224ed9b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839238"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>İzlenecek yol: LinqToXmlDataBinding örneği
Bu izlenecek yolda LinqToXmlDataBinding örneği ve iki birincil kaynak dosyalarından daha ilgi çekici içeriğini bazıları açıklanmaktadır *L2DBForm.xaml* ve *L2DBForm.xaml.cs*.

## <a name="prerequisites"></a>Önkoşullar
 Bu kılavuzu okumadan önce derleme ve açıklandığı gibi LinqToXmlDataBinding programı çalıştırın öneririz [nasıl yapılır: derleme ve çalıştırma LinqToXmlDataBinding örneği](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Açıklamalar
 Oluşan bir Windows Presentation Foundation (WPF) uygulaması C# ve XAML kaynak dosyaları LinqToXmlDataBinding programdır. Kitap listesi tanımlar ve görüntüleme, ekleme, silme ve bu girişleri düzenlemek kullanıcının sağlayan gömülü bir XML belgesi içeriyor. Bunu, aşağıdaki iki birincil kaynak dosyalardan oluşur:

- *L2DBForm.XAML* ana penceresinin kullanıcı arabirimi (UI) XAML bildirimi kodunu içerir. Ayrıca, bir veri sağlayıcısı ve kitap listeleri için katıştırılmış XML belgesi tanımlayan bir pencere kaynak bölümü içerir.

- *L2DBForm.xaml.cs* başlatma ve kullanıcı Arabirimi ile ilişkili olay işleme yöntemleri içerir.

  Ana pencereyi aşağıdaki dört dikey UI bölümlere ayrılmıştır:

- **XML** ham XML kaynağını katıştırılmış kitap listesi görüntüler.

- **Kitap listesi** defteri girdileri standart metin olarak görüntüler ve seçin ve tek tek girişleri silmek sağlar.

- **Seçili kitap Düzenle** seçili rehberi girişiyle ilişkili değerlerini düzenlemek kullanıcının sağlar.

- **Yeni kitabı ekleme** kullanıcı tarafından girilen değerleri temel alarak yeni bir kitap giriş oluşturulmasını sağlar.

## <a name="in-this-section"></a>Bu bölümde

|Konu|Açıklama|
|-----------|-----------------|
|[L2DBForm.xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md)|İçeriği ve XAML kodu dosyasında L2DBForm.xaml açıklamasını içerir.|
|[L2DBForm.xaml.cs kaynak kodu](../designers/l2dbform-xaml-cs-source-code.md)|İçeriği ve C# kaynak kodu dosyasında L2DBForm.xaml.cs açıklamasını içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ, XML örneği kullanarak WPF verilerini bağlama](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Nasıl yapılır: LinqToXmlDataBinding oluşturma ve çalıştırma örneği](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)