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

### Tampilan / Screenshot

**Dashboard Headlamp**

![Dashboard](./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2014.30.54.jpeg)

_Keterangan: Headlamp untuk memudahkan melakukan monitoring sumberdaya_

---

**Map Node Headlamp**

![Map Node](./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2014.02.13.jpeg)

_Keterangan: Skema node cluster_

---

**Detail login-app deployment**

![Map Node: login-app](<./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2014.02.13(1).jpeg>)

_Keterangan: 3 pod replica dari login-app merupakan tujuan dari project ini dengan mengubah jumlah replica pada web-deployment_
![](./pict-task-documentation/Screenshot%202026-04-20%20143807.png)

---

**Halaman login-app**

![Map Node: login-app](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.12.38.jpeg>)

_Keterangan: Tampilan dari login app yang meminta pengguna untuk memasukkan autentikasi agar bisa mengakses halaman dashboard_

![Map Node: login-app](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.13.01.jpeg>)

_Keterangan: Tampilan dari halaman dashboard_
