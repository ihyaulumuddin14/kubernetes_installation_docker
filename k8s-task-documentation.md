# 📁 [Kubernetes : Cluster Management]

> _Manajemen cluster Kubernetes_

---

## 👥 Daftar Anggota Kelompok

| No  | Nama Lengkap           | NIM             |
| --- | ---------------------- | --------------- |
| 1   | Ihya' Ulumuddin        | 245150201111024 |
| 1   | Muhammad Fatih Alhakim | 245150200111047 |

- **Kelas :** A
- **Mata Kuliah :** Penyediaan Automasi Layanan
- **Dosen :** Widhi Yahya, S.Kom., M.T., M.Sc., Ph.D.

---

## 📌 Deskripsi Project

Project ini bertujuan untuk melakukan manajemen klaster menggunakan Kubernetes (K8S) dengan cara menginstalasi environment K8S berbasis Docker, kemudian melakukan deployment aplikasi sebanyak 3 replicas. Melalui project ini, kami mempelajari bagaimana Kubernetes mengotomasi pembuatan dan pengelolaan pod, sehingga aplikasi dapat berjalan secara andal dan mudah di-scale.

---

## 🎯 Tujuan Project

1. memahami cara menyiapkan environment K8S menggunakan Docker, mulai dari clone repo, konfigurasi, hingga cluster bisa berjalan.
2. memahami konsep dasar K8S yaitu:
   - Deployment → cara mendeploy aplikasi di atas klaster
   - Replicas → K8S bisa menjalankan beberapa instance aplikasi sekaligus, sehingga kalau satu pod mati, yang lain tetap jalan (high availability)

---

## 🖼️ Hasil Project

Pada projek ini, kami menambahkan konfigurasi nginx sebagai reverse proxy agar dapat mengakses dua layanan yang berbeda dari satu domain tanpa menuliskan port internal secara eksplisit pada kolom url.

```bash
   server {
      listen 80;
      server_name pal-uund.bccdev.id;

      location / {
         proxy_pass http://10.202.0.33:30080;
         proxy_set_header Host $host;
         proxy_set_header X-Real-IP $remote_addr;
         proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
         proxy_set_header X-Forwarded-Proto $scheme;

         client_max_body_size 5M;
         proxy_read_timeout 90;
      }

      location /headlamp {
         return 301 /headlamp/;
      }

      location /headlamp/ {
         proxy_pass http://10.202.0.33:31873;

         proxy_set_header Host $host;
         proxy_set_header X-Real-IP $remote_addr;
         proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
         proxy_set_header X-Forwarded-Proto $scheme;
         proxy_set_header X-Forwarded-Prefix /headlamp;

         proxy_http_version 1.1;
         proxy_set_header Upgrade $http_upgrade;
         proxy_set_header Connection "upgrade";
      }
   }
```

### Tampilan / Screenshot

**Dashboard Headlamp**

![Dashboard](./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2016.34.00.jpeg)

_Keterangan: Tampilan dashboard headlamp ketika mengakses route /headlamp_

_Setelah berhasil menginstall kubernetes dan mendeploy aplikasi, selanjutnya instalasi dashboard kubernetes untuk memudahkan memonitoring resource, sayanganya dashboard dari kubernetes sudah deprecated, oleh karena itu kami menggunakan Headlamp dashbooard sebagai alternatifnya._

---

**Map Node Headlamp**

![Map Node](./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2014.02.13.jpeg)

_Keterangan: Skema cluster kubernetes_

_Skema pada gambar merupakan visualisasi dari cluster kubernetes yang terdiri dari 2 node utama yaitu ulum-k8s-master sebagai master dan ulum-k8s-worker sebagai worker_

_Node ulum-k8s-master merupakan `Control Plane`, yaitu node yang mengelola sistem cluster seperti membuat keputusan penjadwalan serta mendeteksi dan menanggapi peristiwa yang terjadi di dalam cluster._

_Sedangkan nde ulum-k8s-worker adalah `Data Plane` yang merupakan node untuk mengelola resource dan aplikasi (pod). Fungsi dari node ini berupa eksekusi dan penyediaan resource, seperti menjalankan kontainer (Container Runtime), melankasanakan perintah dari node master (Kubelet), dan pengelola jaringan (Kube-proxy) agar pod bisa berkomunikasi atau bisa diakses di luar cluster._

---

**Detail login-app deployment**

![Map Node: login-app](<./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2014.02.13(1).jpeg>)

_Keterangan: Gambar diatas merupakan Dependency map dari aplikasi login-app_

_Pada gambar tersebut terdaapt 3 pod replica dari login-app yang berjalan secara paralel yang mana merupakan tujuan dari project ini dengan mengubah jumlah replica pada web-deployment berikut:_

![](./pict-task-documentation/Screenshot%202026-04-20%20143807.png)

_Ke tiga pod tersebut adalah pengaplikasian dari high availability, yang mana jika terdapat satu pod yang mati/error, dua pod lainnya masih dapat melayani user selama pod baru yang sehat di buat kembali oleh ReplicaSet._

_Karena kemungkinan besar terjadinya perubahan IP pada pod yang disebabkan error atau mati, maka terdapat Service login-app sebagai load balancer internal yang terhubung ke ketiga pod memiliki fungsi untuk memberikan satu IP/DNS yang statis._

---

**Halaman login-app**

![Map Node: login-app](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.12.38.jpeg>)

_Keterangan: Tampilan dari aplikasi login-app (pod) yang merupakan route utama dari domain yang meminta pengguna untuk memasukkan autentikasi agar bisa mengakses halaman dashboard._

![Map Node: login-app](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.13.01.jpeg>)

_Keterangan: Tampilan dari halaman dashboard._

![Map Node: login-app](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.15.39.jpeg>)

_Keterangan: Tampilan ketika mengupload gambar._

![Map Node: login-app](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.16.22.jpeg>)

_Keterangan: Tampilan dari halamaan ketika berhasil mengupload ke database._

![Map Node: login-app](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.22.02.jpeg>)

_Keterangan: gambar yang berhasil diupload akan tersimpan ke dalam database._
