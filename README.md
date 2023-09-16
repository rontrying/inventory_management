1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
    1. Membuat sebuah proyek Django baru.
        - hal ini saya lakukan dengan membuat sebuah direktori baru kemudian dilanjutkan dengan membuat lingkungan virtual, setelah itu saya menginstal modul modul yang diperlukan, kemudian dilanjutkan dengan membuat proyek django. Saya mengatur ALLOWED_HOSTS di settings.py untuk keperluan deployment dan jadi proyek django baru
    2. Membuat aplikasi dengan nama main pada proyek tersebut.
        - saya menjalankan perintah python manage.py startapp main, kemudian saya mendaftarkannya pada file settings.py dengan menambahkannya ke dalam variabel INSTALLED_APPS
    3. Membuat model pada aplikasi main dengan nama Item dan memiliki atribut wajib.
        - saya membuka berkas models.py pada direktori aplikasi main, kemudian saya mengisi berkas tersebut dengan model bernama item beserta atribut wajibnya seperti name sebagai nama item dengan tipe CharField, amount sebagai jumlah item dengan tipe IntegerField dan description sebagai deskripsi item dengan tipe TextField. Terakhir saya lakukan migrasi model dan migrasi ke dalam basis data lokal.
    4. Membuat sebuah fungsi pada views.py untuk dikembalikan ke dalam sebuah template HTML yang menampilkan nama aplikasi serta nama dan kelas kamu.
        - mengimport modul yang telah diinstall kemudian menambahkan fungsi untuk mengambil 2 variabel yang kemudian akan dikirimkan ke templete main.html sebagai konteks bagi laman web. Terakhir saya membuat 2 variabel tersebut menjadi statis sesuai dengan sintaks django agar dapat menampilkan nilai dari fungsi
    5. Membuat sebuah routing pada urls.py aplikasi main untuk memetakan fungsi yang telah dibuat pada views.py
        - diawal saya melakukan konfigurasi routing URL aplikasi main dengan menambahkan url patterns path('', show_main, name='show_main') kemudian saya juga lakukan konfigurasi urls.py pada proyek
    6. Melakukan deployment ke Adaptable terhadap aplikasi yang sudah dibuat sehingga nantinya dapat diakses oleh teman-temanmu melalui Internet.
        - setelah memastikan semua langkah telah berjalan selanjutnya saya lakukan git add, commit dan push lalu saya deploy app saya, dengan memilih templete, database, dan versi python yang sesuai, tidak lupa menambahkan commandnya di adaptable. Aplikasi sudah bisa dilihat oleh teman teman.

2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html
    ![Gambar](/pbpbagan.png)
    Dalam pengembangan web menggunakan Django, terdapat beberapa berkas yang saling terkait, yaitu urls.py, views.py, models.py, dan berkas HTML. 

    urls.py dengan views.py, Berkas ini berisi daftar URL yang dapat diakses oleh pengguna. Berkas ini berfungsi sebagai penghubung antara URL dan view dimana setiap url diarahkan ke view yang ada di views.py. Saat pengguna mengakses URL tertentu, Django akan mencari URL tersebut di berkas urls.py dan mengarahkannya ke view yang sesuai. views.py dengan models.py: Berkas ini berisi fungsi-fungsi yang mengatur logika pada aplikasi web. Setiap view menerima request dari pengguna dan memberikan response yang sesuai. View dapat mengakses data dari models.py dan mengirimkan data tersebut ke berkas HTML. View juga dapat melakukan operasi CRUD (Create, Read, Update, Delete) pada data. Models.py dengan database: models.py menjembatani pertukaran data untuk views.py. Berkas HTML: Berkas ini berisi kode HTML, CSS, dan JavaScript yang digunakan untuk menampilkan halaman web kepada pengguna. Berkas ini menerima data dari view dan menampilkan data tersebut ke pengguna. Berkas ini juga dapat menerima input dari pengguna dan mengirimkannya kembali ke view.


3. Jelaskan mengapa kita menggunakan virtual environment?
    - kita menggunakan virtual environment untuk menyediakan ruangan bagi proyek kita sendiri ini membantu kita dalam isolasi package serta dependencies dari proyek kita yang lain, setiap ruangan proyek mungkin saja membutuhkan versi library, package serta dependencies yang berbeda beda misal python 3.10 dengan python 3.9 memiliki fitur yang berbeda

3. Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment?
    - ya bisa, meski demikian tetap disarankan untuk kita menggunakan virtual environment hal ini untuk menghindari hal hal yang tidak kita inginkan seperti update library yang bertabrakan, update package untuk menyebabkan salah satu proyek kita dapat tidak berjalan dengan baik, hal tersebut juga dapat terjadi saat kita ingin mengupdate dependencies pada library kita.

4. Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya.
    - Model View Controller (MVC) MVC merupakan pola desain perangkat lunak yang sering digunakan oleh pengembang perangkat lunak. Ini memiliki tiga komponen, masing-masing dengan tujuan tertentu:
    Model: bertugas sebagai pengelola data, logika, dan batasan aplikasi lainnya.
    View : berkaitan dengan bagaimana data akan ditampilkan kepada pengguna dan bertanggung jawab terhadap berbagai komponen representasi data.
    Controller : mengatur interaksi model dan menghubungkan model dan view

    - Model View Template (MVT) MVT adalah pola desain lain yang mirip dengan MVC. Ini juga digunakan untuk mengimplementasikan antarmuka web dan aplikasi, namun berbeda dengan MVC, bagian pengontrol ditangani oleh kerangka kerja itu sendiri. Ini memiliki tiga komponen, masing-masing dengan tujuan tertentu:
    Model: bertugas sebagai pengelola data, dan penghubung ke interface client dan database
    View : berkaitan dengan bagaimana data akan ditampilkan kepada pengguna dan bertanggun jawab terhadap berbagai komponen representasi data.
    Template: mendefinisikan bagaimana data akan disajikan kepada pengguna.

    - Model View ViewModel (MVVM) MVVM adalah implementasi yang lebih spesifik untuk platform pengembangan UI. Ini memiliki tiga komponen, masing-masing dengan tujuan tertentu:
    Model: mirip dengan model yang digunakan di MVC, terdiri dari data dasar yang diperlukan untuk menjalankan perangkat lunak.
    View : antarmuka grafis antara pengguna dan pola desain, mirip dengan yang ada di MVC. Ini menampilkan output dari data yang diproses.
    ViewModel: abstraksi Tampilan, yang menyediakan pembungkus untuk mengikat data model. Ini terdiri dari Model yang diubah menjadi Tampilan dan berisi perintah.
    
    Singkatnya, perbedaan utama antara MVC, MVT, dan MVVM terletak pada cara keduanya memisahkan tanggung jawab visualisasi, pemrosesan, dan pengelolaan data untuk aplikasi UI. Pada MVC Tampilan terbatas pada menampilkan data dan mendelegasikan input pengguna ke Pengontrol. Namun, pola ini sering kali menyebabkan Pengendali menjadi membengkak, sehingga sulit untuk dikelola, sedangkan pada MVT tampilan menjadi lebih pasif namun mendelegasikan masukan dan peristiwa pengguna ke templete, yang memperbarui Model dan Tampilan sesuai dengan itu. Hal ini memisahkan Tampilan dan Model, sehingga membuat sistem lebih mudah dipelihara dan diuji, sedangkan pada MVVM tampilan dirancang secara deklaratif, dalam markup, dengan ViewModel bertanggung jawab untuk menyediakan dan memanipulasi data agar sesuai dengan Tampilan. Pola ini menyederhanakan pengembangan UI, meningkatkan kemampuan pengujian, dan memungkinkan pemisahan logika terkait UI dengan lebih baik.

Referensi 
1. https://id.strephonsays.com/what-is-the-difference-between-mvc-and-mvvm 
2. https://www.localstartupfest.id/faq/perbedaan-mvc-dan-mvvm/ 
3. https://stackoverflow.com/questions/23591580/the-connection-between-django-projects-urls-py-and-views-py 


Tugas 3
1. Apa perbedaan antara form POST dan form GET dalam Django?

    Form GET dan Form POST adalah salah satu metode pengiriman data dari client (biasanya dalam bentuk formulir web) ke server web. Ini adalah salah satu metode yang digunakan dalam protokol HTTP (Hypertext Transfer Protocol) untuk mengirim data dari browser web ke server.
    Dalam Django, form POST dan form GET adalah dua metode pengiriman data dari client side menuju server side. Berikut adalah perbedaan antara keduanya:
        - POST mengirimkan data secara langsung, sedangkan GET mengirimkan data tidak langsung.
        - POST tidak menampilkan nilai variabel di URL, sehingga lebih aman, sedangkan GET menampilkan nilai variabel di URL, sehingga user dapat dengan mudah memasukkan nilai.
        - POST tidak dibatasi panjang string, sedangkan GET dibatasi panjang string sampai 2047 karakter.
        - Pengambilan variabel dengan `request.POST.get` untuk POST dan `request.GET.get` untuk GET.

    Dalam penggunaannya, GET dan POST adalah satu-satunya metode HTTP yang digunakan dalam pengiriman form. Pada umumnya, metode POST digunakan untuk mengubah status sistem, seperti mengubah database, sedangkan metode GET digunakan untuk hal-hal seperti form pencarian.

2. Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data?

    Dalam konteks pengiriman data, XML, JSON, dan HTML memiliki perbedaan utama sebagai berikut:
    - XML (Extensible Markup Language) adalah bahasa markah yang digunakan untuk menyimpan dan mengangkut data dari satu aplikasi ke aplikasi lain melalui Internet. XML digunakan untuk merepresentasikan data dengan cara yang dapat dibaca mesin dan manusia. XML digunakan dalam konteks bisnis dan menyediakan banyak kemampuan dalam hal pemrosesan, validasi, dan transformasi data. XML sendiri menggunakan sintaks tag pembuka dan penutup dengan aturan hierarki.

    - JSON (JavaScript Object Notation) adalah format pertukaran data ringan yang jauh lebih mudah bagi komputer untuk mengurai data yang sedang dikirim. JSON digunakan untuk menyimpan dan mengirimkan data. JSON mendukung angka, objek, string, dan array Boolean. JSON mendukung semua tipe data JSON dan tipe-tipe tambahan. JSON sendiri memiliki sintaks yang menggabungkan nama-nilai yang dikelompokan dalam objek dan larik sehingga berbasis objek.

    - HTML (Hypertext Markup Language) adalah bahasa markah yang digunakan untuk membuat halaman web. HTML digunakan untuk menampilkan data secara visual di browser. HTML digunakan untuk menampilkan data yang telah diolah oleh server dan dikirim ke browser dalam bentuk halaman web. HTML juga menggunakan sintaksis berbasis tag, tetapi tujuannya adalah untuk menggambarkan struktur dan tampilan halaman web, bukan data mentah.

    Dalam pengiriman data, JSON lebih sering digunakan dalam pengembangan aplikasi web saat ini, terutama saat bekerja dengan teknologi AJAX (Asynchronous JavaScript and XML). JSON lebih mudah dibaca dan dimengerti oleh manusia karena formatnya lebih sederhana. JSON juga mendukung semua browser dan semua JavaScript frameworks utama menawarkan dukungan JSON. Sebagian besar teknologi backend mendukung JSON. Sedangkan XML lebih sering digunakan dalam layanan perangkat lunak dan pengiriman pesan. Meskipun ada perbedaan antara format data XML dan JSON, keduanya tetap merupakan bagian yang penting dari pengembangan aplikasi web. Pilihan antara XML atau JSON harus bergantung pada kebutuhan dan spesifikasi proyek.

3. Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern?
    JSON sering digunakan dalam pertukaran data antara aplikasi web modern karena beberapa alasan. 
    
    1. JSON memiliki format yang lebih sederhana dan mudah dipahami oleh manusia dibandingkan dengan format lain seperti XML.
    2. JSON lebih ringan dan lebih cepat dalam pemrosesan data karena memiliki baris kode yang lebih sedikit.
    3. hampir semua browser modern dapat memproses data JSON dengan lancar, sehingga JSON lebih mudah diakses dan lebih fleksibel dalam penggunaannya.
    4. JSON mendukung semua tipe data JSON dan tipe-tipe tambahan, sehingga memudahkan dalam pengolahan data. Oleh karena itu, JSON menjadi pilihan yang lebih sering digunakan dalam pertukaran data antara aplikasi web modern, terutama saat bekerja dengan teknologi AJAX (Asynchronous JavaScript and XML).
    5. JSON sangat mirip dengan javascript sehingga cocok untuk komunikasi antar web dan tidak perlu mengkonversi tipe data. 
    6. JSON mendukung tipe data besar tetapi JSON hanya mendukung serangkaian tipe data secara terbatas, seperti angka, array, dan objek, sehingga memudahkan dalam pengolahan data yang besar dan kompleks. JSON juga mendukung struktur data yang kompleks, seperti dalam bentuk array, sehingga developer dapat menjadikan berbagai data memiliki format yang terstruktur. 
    7. JSON memiliki beberapa fitur keamanan yang memastikan bahwa data yang dikirimkan melalui JSON aman dari serangan. Salah satu fitur keamanan JSON adalah JSON Web Token (JWT), yang digunakan untuk mengamankan RESTful web service. JWT menggunakan HMAC SHA-512 untuk mengenkripsi data, sehingga data yang dikirimkan melalui JSON tetap aman dari serangan. Selain itu, JSON juga mendukung Content Security Policy (CSP), yang memungkinkan pengguna untuk mengontrol sumber daya yang dapat dimuat oleh halaman web. CSP memungkinkan pengguna untuk membatasi sumber daya yang dapat dimuat oleh halaman web, seperti gambar, script, dan CSS, sehingga meminimalkan risiko serangan XSS (Cross-Site Scripting). JSON juga mendukung sintaks format penemuan keamanan (ASFF), yang memungkinkan pengguna untuk menemukan temuan keamanan dalam format JSON.
    8. JSON memiliki efisiensi yang baik dalam hal penggunaan bandwidth karena formatnya yang ringan dan mudah diproses.

4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
    1. mengatur Routing dari main/ ke /
        - pertama tama saya jalankan virtual environment terlebih dahulu di cmd direktori saya
            ```cmd
            env\Scripts\activate.bat
            ```
        - selanjutnya saya buka urls.py yang ada pada folder inventory_management dan mengubah main/ menjadi '' pada urlpatterns seperti berikut
            ```python
            urlpatterns = [
                path('', include('main.urls')),
                path('admin/', admin.site.urls),
            ]
            ```

    2. Implementasi Skeleton sebagai Kerangka Views
        - pertama tama saya membuat folder templates pada root folder dan buatlah sebuah berkas HTML baru bernama base.html. Berkas base.html berfungsi sebagai template dasar yang dapat digunakan sebagai kerangka umum untuk halaman web lainnya di dalam proyek. saya mengisi berkas base.html tersebut dengan kode berikut
            ```html
            {% load static %}
            <!DOCTYPE html>
            <html lang="en">
                <head>
                    <meta charset="UTF-8" />
                    <meta
                        name="viewport"
                        content="width=device-width, initial-scale=1.0"
                    />
                    {% block meta %}
                    {% endblock meta %}
                </head>

                <body>
                    {% block content %}
                    {% endblock content %}
                </body>
            </html>
            ```
        - selanjutnya saya membuka settings.py yang ada pada subdirektori shopping_list dan mencari baris yang mengandung TEMPLATES. saya sesuaikan kode yang ada dengan potongan kode berikut agar berkas base.html terdeteksi sebagai berkas template.
            ```python
            ...
            TEMPLATES = [
                {
                    'BACKEND': 'django.template.backends.django.DjangoTemplates',
                    'DIRS': [BASE_DIR / 'templates'], # Tambahkan kode ini
                    'APP_DIRS': True,
                ...
                }
            ]
            ...
            ```

        - kemudian pada subdirektori templates yang ada pada direktori main, saya mengubah kode berkas main.html yang telah dibuat di tutorial sebelumnya menjadi sebagai berikut.
            ```html
            {% extends 'base.html' %}

            {% block content %}
                <h1>Shopping List Page</h1>

                <h5>Name:</h5>
                <p>{{name}}</p>

                <h5>Class:</h5>
                <p>{{class}}</p>
            {% endblock content %}
            ```

        3. Membuat Form Input Data dan Menampilkan Data Produk Pada HTML
        - pertama saya membuat berkas baru pada direktori main dengan nama forms.py untuk membuat struktur form yang dapat menerima data produk baru. saya menambahkan kode berikut ke dalam berkas forms.py
            ```python
            from django.forms import ModelForm
            from main.models import Item

            class ItemForm(ModelForm):
                class Meta:
                    model = Item
                    fields = ["name", "amount", "description"]
            ```

        - kedua saya buka berkas views.py yang ada pada folder main dan tambahkan beberapa import berikut pada bagian paling atas.






5. Mengakses kelima URL di poin 2 menggunakan Postman, membuat screenshot dari hasil akses URL pada Postman, dan menambahkannya ke dalam README.md.
