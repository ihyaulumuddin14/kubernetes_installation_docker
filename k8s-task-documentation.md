# 📁 Penyediaan dan Automasi Layanan

## 👥 Daftar Anggota Kelompok

| No  | Nama Lengkap           | NIM             |
| --- | ---------------------- | --------------- |
| 1   | Ihya' Ulumuddin        | 245150201111024 |
| 2   | Muhammad Fatih Alhakim | 245150200111047 |

- **Kelas :** A
- **Mata Kuliah :** Penyediaan Automasi Layanan
- **Dosen :** Widhi Yahya, S.Kom., M.T., M.Sc., Ph.D.

---

# 📁 Kubernetes : Cluster Management

## 📌 Deskripsi Project

Project ini bertujuan untuk melakukan manajemen klaster menggunakan Kubernetes (K8s) dengan cara menginstalasi environment K8s berbasis Docker, kemudian melakukan deployment aplikasi sebanyak 3 replicas. Melalui project ini, kami mempelajari bagaimana Kubernetes mengotomasi pembuatan dan pengelolaan pod, sehingga aplikasi dapat berjalan secara andal dan mudah di-scale.

---

## 🎯 Tujuan Project

1. Memahami cara menyiapkan environment K8s menggunakan Docker, mulai dari clone repo, konfigurasi, hingga cluster bisa berjalan.
2. Memahami konsep dasar K8s yaitu:
   - Deployment → cara mendeploy aplikasi di atas klaster
   - Replicas → K8s bisa menjalankan beberapa instance aplikasi sekaligus, sehingga kalau satu pod mati, yang lain tetap jalan (high availability)

---

## 🖼️ Hasil Project

### Tampilan / Screenshot

**Dashboard Headlamp**

![Dashboard](./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2016.34.00.jpeg)

_Keterangan: Tampilan dashboard headlamp ketika mengakses route /headlamp_

_Setelah berhasil menginstall kubernetes dan mendeploy aplikasi, selanjutnya instalasi Kubernetes dashboard untuk memudahkan memonitoring resource. Berdasarkan dokumentasi resmi dari Kubernetes, kubernetes dashboard telah deprecated, oleh karena itu kami menggunakan Headlamp dashbooard sebagai alternatifnya._

---

**Map Node Headlamp**

![Map Node](./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2014.02.13.jpeg)

_Keterangan: Skema cluster kubernetes_

_Skema pada gambar merupakan visualisasi dari cluster kubernetes yang terdiri dari 2 node utama yaitu ulum-k8s-master sebagai master dan ulum-k8s-worker sebagai worker_

_Node ulum-k8s-master merupakan `Control Plane`, yaitu node yang mengelola sistem cluster seperti membuat keputusan penjadwalan serta mendeteksi dan menanggapi peristiwa yang terjadi di dalam cluster._

_Sedangkan node ulum-k8s-worker adalah `Data Plane` yang merupakan node untuk mengelola resource dan aplikasi (pod). Fungsi dari node ini berupa eksekusi dan penyediaan resource, seperti menjalankan kontainer (Container Runtime), melaksanakan perintah dari node master (Kubelet), dan pengelola jaringan (Kube-proxy) agar pod bisa berkomunikasi atau bisa diakses di luar cluster._

---

**Detail login-app deployment**

![Map Node: login-app](<./pict-task-documentation/WhatsApp%20Image%202026-04-20%20at%2014.02.13(1).jpeg>)

_Keterangan: Gambar diatas merupakan Dependency map dari aplikasi login-app_

_Pada gambar tersebut terdapat 3 pod replica dari login-app yang berjalan secara paralel yang mana merupakan tujuan dari project ini dengan mengubah jumlah replica pada web-deployment berikut:_

![](./pict-task-documentation/Screenshot%202026-04-20%20143807.png)

_Ketiga pod tersebut adalah penerapan dari prinsip high availability, yang mana jika terdapat satu pod yang mati/error, dua pod lainnya masih dapat melayani user selama pod baru yang sehat di buat kembali oleh ReplicaSet._

_Karena kemungkinan besar terjadinya perubahan IP pada pod yang disebabkan error atau mati, maka terdapat Service login-app sebagai load balancer internal yang terhubung ke ketiga pod memiliki fungsi untuk memberikan satu IP yang statis sehingga lebih stabil daripada menggunakan IP pod karena akan menghasilkan IP baru ketika terdapat pod baru._

---

**Halaman login-app**

![](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.12.38.jpeg>)

_Keterangan: Tampilan dari aplikasi login-app (pod) yang merupakan route utama dari domain yang meminta pengguna untuk memasukkan autentikasi agar bisa mengakses halaman dashboard._

![](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.13.01.jpeg>)

_Keterangan: Tampilan dari halaman dashboard._

![](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.15.39.jpeg>)

_Keterangan: Tampilan ketika mengupload gambar._

![](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.16.22.jpeg>)

_Keterangan: Tampilan dari halaman ketika berhasil mengupload ke database._

![](<./pict-task-documentation/WhatsApp Image 2026-04-20 at 16.22.02.jpeg>)

_Keterangan: gambar yang berhasil diupload akan tersimpan ke dalam database._

Project ini bertujuan membangun sistem aplikasi yang andal di Kubernetes dengan dua fokus utama: pemerataan trafik (load balancing) dan pemantauan performa secara real-time (monitoring). Implementasi dilakukan dengan deployment multi-replica, Service dan Ingress untuk distribusi request antar pod, serta integrasi Metrics Server, Prometheus, dan Grafana untuk mengumpulkan, memvisualisasikan, dan menganalisis metrik resource aplikasi/cluster. Melalui pengujian beban dan HPA (Horizontal Pod Autoscaler), project ini membuktikan bahwa sistem mampu merespons peningkatan trafik secara otomatis, menjaga ketersediaan layanan, dan menyediakan data observabilitas untuk troubleshooting serta pengambilan keputusan operasional.

---

# 📁 Kubernetes : Monitoring dan Load Balancing

## 📌 Deskripsi Project

Project ini bertujuan membangun sistem aplikasi yang andal di Kubernetes dengan dua fokus utama: pemerataan trafik (load balancing) dan pemantauan performa secara real-time (monitoring). Implementasi dilakukan dengan deployment multi-replica, Service dan Ingress untuk distribusi request antar pod, serta integrasi Metrics Server, Prometheus, dan Grafana untuk mengumpulkan, memvisualisasikan, dan menganalisis metrik resource aplikasi/cluster. Melalui pengujian beban dan HPA (Horizontal Pod Autoscaler), project ini membuktikan bahwa sistem mampu merespons peningkatan trafik secara otomatis, menjaga ketersediaan layanan, dan menyediakan data observabilitas untuk troubleshooting serta pengambilan keputusan operasional.

---

## 🎯 Tujuan Project

1. Menunjukkan bahwa load balancing bekerja dengan baik
2. Menunjukkan bahwa monitoring dan autoscaling bekerja

---

## 🖼️ Hasil Project

### Tampilan / Screenshot

#### Monitoring

**Deploy Metrics**

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2011.27.25.jpeg)

_Keterangan: Server metrics berjalan_

_Metrics menyediakan informasi sumber daya yang digunakan oleh setiap node dan pod berupa berapa lama penggunaan CPU dan seberapa besar kapasistas memory yang digunakan._

---

**Prometheus dan Grafana**

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2010.01.39.jpeg)
![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2010.02.34.jpeg)

_Keterangan: Komponen Prometheus dan Grafana_

_Gambar menunjukkan stack monitoring promethus dan grafana sudah berhasil dipasang dan berjalan dengan baik._

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2010.05.05.jpeg)

_Keterangan: Grafana Dashboard (Kubernetes Deployment)_

_Gambar menunjukkan tampilan dari dashboard kubernetes deployment yang memiliki ID 8588 yang memiliki nama Kubernetes Deployment Statefulset Daemonset metrics._

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2010.04.05.jpeg)

_Keterangan: mengakses /metrics yang menunjukkan endpoint metrics dapat diakses_

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2010.06.19.jpeg)

_Keterangan: Grafana Custom Dashboard_

_Gambar menunjukkan tampilan dari dashboard kustom yang berupa informasi metrics, nama dashboard ini adalah Network metrics Dasshboard yang menampilkan panel penggunaan CPU dan memory oleh 3 replica pod._

_Dengan mengikuti langkah langkah Prometheus-Grafana.md, panel Network Transmitted dan Network Preceived tidak memunculkan informasi apapun._

---

**Monitoring Autoscaling**

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2016.29.01.jpeg)

_Keterangan: Load testing menggunakan hey_
_Perintah hey -z 5m -c 50 http://<node-ip>:30080/login akan mensimulasikan jika ada 50 request yang berjalan secara bersamaan selama 5 menit ke port 30080 yang mengarah ke login_

_Berdasarkan summary-nya sistem mampu menangani 71.117 request dengan status sukses (200 OK) dengan rata rata kecepatan pemrosesan 294,24 request/second dan rata rata latency pada 172 ms dengan waktu respon tercepat mencapai 0,0011 detik_

_Munculnya error pada 8 respon dengan status 504 (Gateway Timeout) dengan error "connection refused" sebanyak 1.063 kejadian menandakan bahwa meskipun Horizontal Pod Autoscaler (HPA) telah melakukan scaling maksimal hingga 10 replika (sebagaimana dikonfirmasi pada observasi kubectl get hpa), volume trafik yang masuk tetap sempat menyentuh batas ambang kapasitas resource atau antrean pada node yang tersedia._

![](<./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2016.29.01(1).jpeg>)
_Keterangan: Cek status HPA (Horizontal Pod Autoscaler)_

_Berdasarkan log perintah kubectl get hpa -w, tercatat adanya lonjakan penggunaan sumber daya yang sangat signifikan. Penggunaan CPU meningkat dari status stabil/awal hingga menyentuh angka 339%. Nilai ini melampaui batas ambang (threshold) yang telah ditetapkan sebesar 50%_

_Keberhasilan HPA dalam mengubah jumlah replika menjadi 10 menunjukkan bahwa kebijakan scaling telah terkonfigurasi dengan benar. Meskipun sempat muncul status <unknown> sesaat (yang merupakan hal wajar saat proses pembaruan data metrik oleh Metrics Server), HPA tetap mampu mengambil keputusan berdasarkan titik beban tertinggi yang terdeteksi._

![](<./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2016.29.01(2).jpeg>)
_Keterangan: Detail konfigurasi dan status HPA_

_Pada gambar terlihat sistem telah kembali ke kondisi stabil (Scale-Down) setelah pengujian beban selesai, yang mana tercatat 2 current / 2 desired, artinya jumlah pod telah diturunkan kembali ke batas minimal karena penggunaan CPU turun menjadi 4% dan Memori 19%._

_Status ScalingActive bernilai True dengan pesan "the HPA was able to successfully calculate a replica count", yang membuktikan validitas integrasi antara HPA dan Metrics Server._

**Web-deployment.yaml**

```bash
   resources:
   requests:
      cpu: "100m"
      memory: "128Mi"
   limits:
      cpu: "500m"
      memory: "512Mi"
```

_Penerapan resource requests pada web-deployment.yaml sangat krusial karena berfungsi sebagai dasar metrik bagi Horizontal Pod Autoscaler (HPA). Tanpa definisi requests yang jelas, HPA tidak dapat menentukan ambang batas utilisasi, yang mengakibatkan kegagalan mekanisme autoscaling (status <unknown>). Selain itu, limits diterapkan untuk mencegah sebuah pod mengonsumsi sumber daya secara berlebihan yang dapat mengganggu stabilitas pod lain dalam satu node._

---

#### Load Balancing

Pada projek ini, kami mengganti port pada proxy nginx yang sebelumnya adalah 30080 menjadi 30081 karena ingress controller berjalan diatasnya sesuai dengan petunjuk di LB_DEPLOYMENT.

```bash
   server {
      listen 80;
      server_name pal-uund.bccdev.id;

      location / {
         proxy_pass http://10.202.0.33:30081;
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

**Ingress controller running**

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2010.07.53.jpeg)

_Keterangan: kubectl get pods -n ingress-nginx_
_Menunjukkan ingress controller dalam status running_

**Detail Ingress login-app-ingress**

![](./pict-task-documentation/WhatsApp%20Image%202026-04-22%20at%2010.08.26.jpeg)

_Keterangan: kubectl describe ingress login-app-ingress mrupakan perintah yang menghasilkan detail mengenai resource ingress login-app-ingress. NGINX Ingress Controller ini bertindak sebagai Entry Point yang menerjemahkan aturan Ingress (Ingress Rules) menjadi konfigurasi NGINX untuk mengarahkan trafik dari IP Node/LoadBalancer ke Service aplikasi (seperti login-app)_

**Halaman login-app**

<p align="center">
  <img src="./pict-task-documentation/WhatsApp Image 2026-04-22 at 10.12.15(1).jpeg" width="45%" />
  <img src="./pict-task-documentation/WhatsApp Image 2026-04-22 at 10.12.15.jpeg" width="45%" />
</p>

_Keterangan: Bukti aktifnya load balancing_
_Gambar menunjukkan tampilan antarmuka (UI) aplikasi "Image Upload Dashboard" saat diakses oleh pengguna. Fokus utama pada pengujian ini adalah label identitas server di pojok kanan bawah:_

_- Gambar 1: Melayani melalui pod login-app-5c8cc65db-k2nw7._

_- Gambar 2: Melayani melalui pod login-app-5c8cc65db-gnpj9._

_Meskipun pengguna mengakses URL yang sama, sistem secara otomatis mengarahkan request ke pod (replika) yang berbeda. Ini membuktikan bahwa Service Kubernetes (dan Ingress) berhasil menjalankan fungsinya sebagai Load Balancer dan trafik tidak hanya menumpuk pada satu pod saja, melainkan didistribusikan secara merata ke seluruh replika yang sedang berjalan._
