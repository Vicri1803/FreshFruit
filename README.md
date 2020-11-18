# FreshFruit

Aplikasi penjualan buah sederhana

![Diagram](https://user-images.githubusercontent.com/62140544/99487325-a1b9ac80-2998-11eb-89bd-7caf7873011d.JPG)

# Logika Algoritma

        public MainWindow()
        {
            InitializeComponent();

            Bucket keranjangBuah = new Bucket(2);
            BucketController bucketController = new BucketController(keranjangBuah, this);

            vicri = new Seller("vicri", bucketController);

            ListBoxBucket.ItemsSource = keranjangBuah.findAll();
        }

Membuat intance vicri untuk dijadikan seller yg menjalankan progam, dan diberikan akses untuk mengontrol BucketController.cs 

        private void Button1_Click(object sender, RoutedEventArgs e)
        {
            Fruit anggur = new Fruit("Anggur");
            vicri.addFruit(anggur);
        }

        private void Button2_Click(object sender, RoutedEventArgs e)
        {
            Fruit Apel = new Fruit("Apel");
            vicri.addFruit(Apel);

        }
        private void Button3_Click(object sender, RoutedEventArgs e)
        {
            Fruit Pisang = new Fruit("Pisang");
            vicri.addFruit(Pisang);

        }
        private void Button4_Click(object sender, RoutedEventArgs e)
        {
            Fruit jeruk = new Fruit("Jeruk");
            vicri.addFruit(jeruk);

        }
        
Penginisialisasian button untuk buah untuk dimasukkan kedalam keranjang oleh seller.

        public void addFruit(Fruit fruit)
        {
            if (bucketIsOverload())
            {
                eventListener.onFailed("Ops, keranjang penuh");
            }
            else
            {
                this.bucket.insert(fruit);
                eventListener.onSucceed("Yey, berhasil ditambahkan");
            }
        }
        public bool bucketIsOverload()
        {
            return bucket.countItems() >= bucket.getCapacity();
        }
        
Kode progam untuk penambahan dan penghitungan buah yang dimasukkan seller kedalam keranjang. Perhitungan disini menghasilkan output dimana jika keranjang memenuhi kriteria penuh maka akan mengoutputkan sebuah notifikasi, atau masih bisa diisi kembali.

# fungsi bucketeventlistener

    interface BucketEventListener
    {
        void onSucceed(string message);
        void onFailed(string message);
    }
    
 sebagai pendendali dari event keranjang tentang gagal atau berhasilnya proses diatas.
    
