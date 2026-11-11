komputer vision  berbasis CNN (Convolutional Neural Network) deteksi Manusia dan Indikasi Membawa Senjata sebagai Pendukung Pengawasan Satwa Dilindungi

Proyek AI untuk Mendukung Pengawasan Satwa Dilindungi

Proyek ini mengembangkan prototipe deteksi objek yang mengenali manusia dan indikasi manusia yang membawa senjata dari gambar atau video kamera. Hasil deteksi direncanakan ditampilkan dalam bentuk kotak, label, dan skor keyakinan.

Prototipe ini menggambarkan potensi AI untuk mendukung pengawasan satwa dilindungi di masa depan. Proyek ini bukan sistem siap pakai untuk dipasang di hutan dan tidak menentukan apakah seseorang melakukan pelanggaran. Prediksi model merupakan indikasi berdasarkan gambar yang dianalisis, bukan kepastian.

## Latar Belakang

Pengawasan kawasan yang menjadi habitat satwa dilindungi dapat terbantu oleh teknologi yang membantu menandai keberadaan manusia pada gambar kamera. Informasi tersebut dapat menjadi salah satu bahan untuk mengamati potensi aktivitas manusia yang perlu diperhatikan.

Proyek ini membuat prototipe AI yang mendeteksi manusia serta memberikan indikasi ketika manusia tampak membawa senjata. Aplikasi web dirancang untuk menerima gambar dari kamera, memprosesnya secara berkala, lalu menampilkan hasil deteksi. Model tidak harus memeriksa setiap frame, sehingga hasil dapat muncul setelah proses analisis selesai.

Proyek ini merupakan tahap awal untuk menunjukkan alur dan potensi fungsi tersebut. Prototipe ini tidak ditujukan sebagai sistem operasional dan belum membuktikan kinerja di lingkungan hutan.

## Urgensi

Proyek ini penting sebagai demonstrasi awal tentang bagaimana deteksi berbasis AI dapat membantu menampilkan keberadaan manusia dan indikasi membawa senjata pada gambar kamera. Prototipe juga menjadi dasar untuk mempelajari alur pemrosesan dari kamera, model deteksi, hingga penyajian hasil kepada pengguna.

Pengembangan ini dapat menjadi titik awal bagi penelitian lanjutan, seperti memperbaiki anotasi, menambah data, dan menguji model pada kondisi yang lebih beragam. Hasil proyek tidak boleh digunakan sebagai satu-satunya dasar untuk menilai seseorang atau mengambil keputusan di lapangan.

## Tujuan

Melatih model deteksi objek menggunakan dataset *People with Arms* versi 26.

Mendeteksi manusia pada gambar atau video.

Menampilkan indikasi manusia yang dikenali model sebagai manusia yang membawa senjata.

Menampilkan hasil berupa kotak deteksi, label kelas, dan skor keyakinan.

Menjadi prototipe awal yang menggambarkan potensi AI untuk mendukung pengawasan satwa dilindungi di masa depan.

## Dataset

Nama dataset: People with Arms.

Versi: 26.

Sumber: [Roboflow Universe — People with Arms, versi 26](https://universe.roboflow.com/arms-l4rlk/people-with-arms/dataset/26 ).

Jumlah gambar: 5.466 gambar.

Pembagian dataset yang tercantum pada halaman versi 26:

- Data pelatihan: 5.064 gambar.
- Data validasi: 402 gambar.
- Data pengujian: tidak tersedia pada versi ini.

Format dataset untuk pelatihan: YOLOv8.

Lisensi yang tercantum: CC BY 4.0.

Nama dan urutan kelas harus diperiksa dari berkas `data.yaml` setelah dataset diunduh. Kelas yang direncanakan untuk digunakan dalam proyek ini adalah `human`, `human_with_gun`, dan `people-arm`.

## Arti Label untuk Proyek

`human` digunakan sebagai label deteksi manusia atau Person.

`human_with_gun` digunakan sebagai indikasi manusia yang membawa senjata atau Person with Weapon, sesuai anotasi dataset.

`people-arm` dapat digunakan sebagai petunjuk pendukung yang berkaitan dengan area tangan atau senjata yang dipegang. Label ini bukan label gerakan tangan. Arti serta cakupan kotaknya perlu dipahami sesuai anotasi dataset.

Jika model tidak mendeteksi `human_with_gun`, hasilnya berarti “senjata tidak terdeteksi oleh model”. Hal tersebut bukan bukti bahwa orang yang terlihat pasti tidak membawa senjata.

## Metode

Proyek ini menggunakan transfer learning dengan fine-tuning terawasi untuk deteksi objek.

Pelatihan dimulai dari bobot pralatih YOLOv8n (`yolov8n.pt`). Model kemudian disesuaikan menggunakan anotasi dataset *People with Arms* versi 26. Model tidak dilatih dari awal.

## Alur Pengerjaan

Menyiapkan Google Colab dan memilih runtime GPU jika tersedia.

Memasang pustaka yang dibutuhkan untuk menjalankan YOLOv8 dan mengunduh dataset.

Menghubungkan Google Drive untuk menyimpan hasil pelatihan.

Mengunduh dataset versi 26 dari Roboflow dalam format YOLOv8.

Memeriksa `data.yaml`, nama kelas, dan pembagian dataset sebelum pelatihan.

Melatih YOLOv8n menggunakan data pelatihan.

Memantau proses pelatihan dan menyimpan bobot model terbaik.

Mengevaluasi model pada data validasi.

Mencoba prediksi pada gambar atau video sebagai demonstrasi awal.

Mengintegrasikan model ke aplikasi web berkamera sebagai tahap pengembangan prototipe.

## Algoritma

Model utama adalah YOLOv8n dari pustaka Ultralytics.

YOLO merupakan model deteksi objek yang memperkirakan lokasi objek pada gambar sekaligus memprediksi kelasnya. Hasil deteksi mencakup kotak pembatas, nama kelas, dan skor keyakinan.

YOLOv8n dipilih sebagai varian ringan untuk percobaan awal. Model menggunakan bobot pralatih, lalu menjalani fine-tuning pada dataset proyek.

## Evaluasi

Evaluasi direncanakan menggunakan data validasi yang disediakan dataset.

Versi dataset yang digunakan tidak mencantumkan data pengujian terpisah. Oleh karena itu, metrik validasi bukan hasil evaluasi pada test set independen.

Nilai metrik belum dicantumkan di README ini karena harus diisi setelah pelatihan dan evaluasi benar-benar dijalankan. Jangan menganggap nilai evaluasi validasi sebagai ukuran pasti kinerja model pada semua gambar atau kondisi.

## Batasan

Proyek ini merupakan prototipe awal untuk tugas kuliah, bukan sistem siap pakai di lapangan.

Versi dataset yang digunakan tidak menyediakan test set terpisah. Hasil validasi memiliki keterbatasan untuk menunjukkan kemampuan model pada data baru.

Prediksi `human_with_gun` merupakan indikasi dari model berdasarkan gambar, bukan kepastian bahwa seseorang membawa senjata.

Jika model tidak mendeteksi senjata, hal tersebut tidak memastikan bahwa orang tersebut tidak membawa senjata.

Dataset berasal dari sumber dan kondisi gambar tertentu. Hasilnya belum membuktikan kinerja pada berbagai kamera, jarak, pencahayaan, atau kondisi lingkungan.

Label `people-arm` merupakan anotasi objek dan tidak menunjukkan urutan atau gerakan tangan dari waktu ke waktu.

Prototipe tidak menentukan apakah seseorang melakukan pelanggaran dan tidak menggantikan penilaian manusia.

## Status Pengembangan

Pelatihan model dilakukan menggunakan Google Colab. Aplikasi web berkamera merupakan bagian dari tujuan prototipe dan baru dapat dianggap selesai setelah implementasi serta pengujiannya dilakukan.

Rancangan aplikasi adalah memproses gambar kamera secara berkala, kemudian menampilkan kotak deteksi, label, dan skor keyakinan. Model tidak harus memproses setiap frame sehingga mungkin ada jeda sebelum hasil muncul.

## Struktur Repository

Struktur berikut merupakan contoh susunan berkas yang dapat digunakan. Sesuaikan nama dan statusnya dengan berkas yang benar-benar tersedia di repository.

```text
.
├── README.md
├── notebook_colab.ipynb
├── best.pt
└── web-app/
