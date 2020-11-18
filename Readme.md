1. Fungsi BucketEventListener adalah menampilkan pesan saat buah di tambahkan ke dalam keranjang
3. Diawali pada `MainWindow.xaml.cs`
 ```csharp
Seller toni;
        public MainWindow()
        {
            InitializeComponent();

            Bucket keranjangBuah = new Bucket(2);
            BucketController bucketController = new BucketController(keranjangBuah, this);

            toni = new Seller("toni", bucketController);

            listBoxBucket.ItemsSource = keranjangBuah.findAll();
        }
```
lalu mendeklarasikan dari instance `Seller` yang telah dibuat tadi
```csharp
private void ButtonAnggur_Click(object sender, RoutedEventArgs e)
        {
            Fruit anggur = new Fruit("Anggur");
            toni.addFruit(anggur);
        }
```
Lalu dalam function ButtonAnggur_Click, digunakan untuk menambahkan item Anggur pada bucket. Sama halnya dengan function ButtonBanana_Click, ButtonApple_Click, dan ButtonOrange_Click.
```csharp
public void onFailed(string message)
        {
            MessageBox.Show(message, "Warning");
        }

        public void onSucceed(string message)
        {
            listBoxBucket.Items.Refresh();
        }
```
Kode yang ada diatas digunakan ketika failed, kemudian masuk ke `model/Seller.cs`, digunakan untuk model atau kerangka atau seller
```csharp
 public List<Fruit> findAll()
        {
            return this.bucket.findAll();
        }

        public void addFruit(Fruit fruit)
        {
            this.bucket.addFruit(fruit);
        }
```
function `findAll ()` digunakan untuk mengambil data dari `bucketController`. Sedangkan `addFruit ()` digunakan untuk menambah data ke `bucketController`
```csharp
public string name { get; set; }

        public Fruit(string name)
        {
            this.name = name;
        }

        public string getName()
        {
            return this.name;
        }