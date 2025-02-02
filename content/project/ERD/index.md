---
title: Entity-Relationship Diagram (ERD) 
date: 2025-01-28
external_link: https://www.figma.com/board/GOWeXaRt41FPfqiL9qFJjz/Bu-nurul?node-id=1842-1079&t=wEmbMFPr2Xs9p1SZ-0
tags:
  - Figma
  - MySql
---
Tugas ini berkaitan dengan perancangan sistem akademik yang mencakup berbagai entitas utama seperti Mahasiswa, Dosen Pembimbing, Dosen Pengampu, KRS, Mata Kuliah, dan Jadwal Mengajar. Diagram ini menggambarkan bagaimana setiap entitas saling berhubungan dalam pengelolaan kegiatan akademik, termasuk proses pengisian KRS, pembimbingan mahasiswa, serta penjadwalan perkuliahan.

Penjelasan Struktur Diagram:
1.Dosen Pembimbing

Memiliki atribut seperti NIDN, Nama Dosen, dan Departemen
Bertugas membimbing mahasiswa
Mahasiswa

2.Memiliki atribut seperti NIM, Nama, dan Prodi
Mengisi KRS (Kartu Rencana Studi) yang berisi informasi tentang kelas, tanggal pengisian, dan status persetujuan
3.KRS (Kartu Rencana Studi)

Merupakan bagian penting dalam proses akademik, di mana mahasiswa memilih mata kuliah yang akan diambil setiap semester
4.Dosen Pengampu

Memiliki atribut seperti NIDN
Mengampu mata kuliah yang akan diambil oleh mahasiswa
5.Mata Kuliah

Memiliki atribut seperti Kode Mata Kuliah, Nama Mata Kuliah, dan Jenis Mata Kuliah
6.Jadwal Mengajar

Berisi informasi tentang hari, jam, dan ruang kelas
Diatur berdasarkan mata kuliah yang diampu oleh dosen
Diagram ini menunjukkan alur sistem akademik, mulai dari mahasiswa mengisi KRS, dosen membimbing mahasiswa, hingga proses perkuliahan yang dijadwalkan dan diampu oleh dosen pengampu. Tugas ini kemungkinan besar bertujuan untuk memahami sistem akademik perguruan tinggi dan bagaimana setiap entitas saling terhubung dalam proses pembelajaran.
<!--more-->
