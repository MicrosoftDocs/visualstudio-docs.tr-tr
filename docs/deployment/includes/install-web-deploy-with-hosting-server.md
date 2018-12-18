Barındırma sunucuları için Web dağıtımı 3.6 arabiriminden yayımlama ayarları dosyası oluşturma ek yapılandırma özellikleri sağlar.

1. Windows Server üzerinde zaten yüklü olan Web dağıtma 3.6 varsa, bunu kullanarak kaldırın **Denetim Masası** > **programlar** > **ProgramKaldır**.

2. Ardından, Windows Server üzerinde barındırma sunucuları için Web dağıtımı 3.6 yükleyin.

    Barındırma sunucuları için Web Dağıtımı'nı yüklemek için kullanın [Web Platformu Yükleyicisi (Webpı)](https://www.microsoft.com/web/downloads/platform.aspx). (Web Platformu yükleyicisi bağlantı IIS'den bulmak için seçin **IIS** Sunucu Yöneticisi'nin sol bölmesinde. Sunucuya sağ tıklayıp **Internet Information Services (IIS) Yöneticisi'ni**.)

    Web Platformu Yükleyicisi'nde bulduğunuz **barındırma sunucuları için Web dağıtımı** uygulamalar sekmesindeki.

3. Zaten yüklemezseniz **IIS Yönetim betikleri ve araçları**, şimdi yükleyin.

    Git **Sunucu Rollerini Seç** > **Web sunucusu (IIS)** > **Yönetim Araçları**ve ardından **IIS Yönetim betikleri ve araçları** rolüne tıklayın **sonraki**ve ardından rolü yükleyin.

    ![IIS Yönetim betikleri ve araçları yükleyin](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Betikleri ve araçları, yayımlama ayarları dosyası oluşturmayı etkinleştirmek için gereklidir.

4. (İsteğe bağlı) Web dağıtımı doğru açarak çalıştığını doğrulayın **Denetim Masası > Sistem ve Güvenlik > Yönetim Araçları > Hizmetleri** emin olun **Web Dağıtım Aracı hizmeti** çalışıyor ( Hizmet eski sürümlerde farklı adıdır).

    Aracı hizmeti çalışmıyorsa başlatın. Hiç yoksa, Git **Denetim Masası > Programlar > program Kaldır**, bulma **Microsoft Web dağıtımı <version>** . Tercih **değişiklik** yükleme ve seçtiğiniz emin **yerel sabit diskinize yüklenecek** Web dağıtımı bileşenleri için. Değişiklik yükleme adımlarını tamamlayın.