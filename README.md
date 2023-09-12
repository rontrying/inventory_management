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
