
1. Güncelleştirilmiş yapılandırma seçenekleri kullanıcı Arabiriminde göstermek için IIS Yönetim Konsolu kapatıp yeniden açın.

2. IIS, sağ **varsayılan Web sitesi**, seçin **Dağıt** > **yapılandırma Web dağıtımı yayımlama**.

    ![Web dağıtımı yapılandırması yapılandırın](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. İçinde **yapılandırma Web dağıtımı yayımlama** iletişim kutusunda, ayarları inceleyin.

4. Tıklayın **Kurulum**.

    İçinde **sonuçları** panelinde erişim haklarını çıkışın gösterdiği belirtilen kullanıcı ve, verilir bir dosyayla bir *.publishsettings* dosya uzantısına oluşturulan iletişim kutusunda gösterilen konuma bir kutu.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Windows Server ve IIS yapılandırmasına bağlı olarak farklı değerler XML dosyasına bakın. Gördüğünüz değerleri ilgili birkaç ayrıntı aşağıdadır:

   * *Msdeploy.axd* başvurulan dosya `publishUrl` Web dağıtımı için dinamik olarak üretilen bir HTTP işleyicisi dosyası bir özniteliktir. (Sınama amacıyla, `http://myhostname:8172` genellikle de çalışır.)
   * `publishUrl` Bağlantı noktası Web dağıtımı için varsayılan bağlantı noktası 8172, ayarlanır.
   * `destinationAppUrl` IIS için varsayılan bağlantı noktası 80 numaralı bağlantı noktası ayarlanır.
   * Visual Studio'da (sonraki adımlarda) konak adını kullanarak uzak ana bilgisayara bağlanmak bulamıyorsanız, ana bilgisayar adı yerine IP adresi test edin.

     > [!NOTE]
     > Bir Azure sanal makinesinde çalışan IIS'ye yayımlıyorsanız, ağ güvenlik grubunda Web dağıtımı ve IIS bağlantı noktalarının açmanız gerekir. Ayrıntılı bilgi için bkz. [yükleme ve çalıştırma IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

5. Bu dosya, Visual Studio'yu çalıştırdığınız bilgisayara kopyalayın.
