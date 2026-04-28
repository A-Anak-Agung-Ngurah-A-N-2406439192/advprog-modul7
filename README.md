## Performance Testing

### Endpoint `/all-student`

![JMeter result all-student](all-student.png)

### Endpoint `/all-student-name`

![JMeter result all-student-name](all-student-name.png)

### Endpoint `/highest-gpa`

![JMeter result highest-gpa](highest-gpa.png)

### Command Line Testing `/all-student-name`

![JMeter CLI result all-student-name](all-student-name-jtl.png)

### Command Line Testing `/highest-gpa`

![JMeter CLI result highest-gpa](highest-gpa-jtl.png)

### Perbandingan Hasil JMeter

Setelah kode dioptimasi, saya menjalankan ulang performance test menggunakan JMeter untuk endpoint `/all-student`, `/all-student-name`, dan `/highest-gpa`. Dari hasil pengujian ulang, ketiga endpoint menunjukkan peningkatan performa dibandingkan dengan hasil pengujian awal.

Peningkatan paling terasa ada pada bagian yang sebelumnya melakukan proses berulang atau mengambil data terlalu banyak dari database. Pada endpoint `/all-student`, query yang sebelumnya dilakukan berkali-kali sudah dikurangi. Pada endpoint `/all-student-name`, aplikasi tidak lagi mengambil seluruh data student karena yang dibutuhkan hanya nama. Untuk endpoint `/highest-gpa`, pencarian GPA tertinggi juga sudah langsung dilakukan lewat repository, sehingga tidak perlu lagi melakukan looping manual di Java.

Dari hasil tersebut, dapat disimpulkan bahwa refactoring yang dilakukan berhasil membuat proses request menjadi lebih ringan dan lebih efisien.