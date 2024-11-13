# Absensi_App

Aplikasi Presensi Mahasiswa Berbasis Python

Aplikasi ini adalah sistem presensi berbasis GUI yang dikembangkan menggunakan Python dengan Tkinter sebagai antarmuka grafis, OpenPyXL untuk manajemen data presensi dalam file Excel, serta OpenCV untuk menangkap gambar. Berikut adalah penjelasan mengenai fitur, paket, dan komponen yang digunakan dalam aplikasi ini.

1. Paket yang Dibutuhkan

from tkinter import *
from tkinter.ttk import Combobox
from tkinter import messagebox
import openpyxl
from openpyxl import Workbook
from openpyxl.styles import Font, Alignment, Border, Side
from tkinter import font as tkfont
import pathlib
import time
from geopy.geocoders import Nominatim
import geocoder
import json
from urllib import request
import os.path
import tkinter as tk
import cv2
from PIL import Image, ImageTk
import util
from fpdf import FPDF
from tkinter import ttk
Deskripsi Paket
Tkinter: Digunakan untuk membuat antarmuka pengguna grafis (GUI).
OpenPyXL: Mengelola data Excel, seperti menyimpan presensi.
geopy & geocoder: Digunakan untuk mendeteksi lokasi pengguna berdasarkan IP.
OpenCV (cv2): Menyediakan fitur kamera untuk pengambilan foto pengguna.
PIL (Python Imaging Library): Memproses dan menampilkan gambar.
FPDF: Menghasilkan file PDF dari data presensi.
2. Struktur Utama Aplikasi

Kelas Utama (App)
Kelas ini berfungsi sebagai inti aplikasi yang mengelola semua fitur presensi, seperti input data, pengaturan lokasi, dan penyimpanan presensi.

a. Inisialisasi (Constructor)

Mengatur tampilan utama (window) dengan ukuran dan tema warna.
Memuat dan mengatur ikon aplikasi.
Mengecek keberadaan file data.xlsx untuk menyimpan data presensi, dan jika file tidak ada, aplikasi membuat file tersebut dengan header kolom yang sesuai.
b. Komponen Label & Entry

Beberapa label dan input entry diletakkan untuk menginput informasi, seperti NIM, nama lengkap, akun Unesa, dan mata kuliah.
Terdapat juga frame untuk menampilkan foto pengguna yang diambil dari kamera.
c. Komponen Dropdown & Tombol

Dropdown Mata Kuliah: Mata kuliah disesuaikan berdasarkan hari. Misalnya, Kalkulus dan Praktikum PD tersedia pada hari Senin.
Tombol Fungsionalitas:
Find🔍 untuk mencari informasi berdasarkan NIM.
Submit untuk mengirim presensi.
Camera 📷 untuk mengaktifkan kamera dan mengambil gambar.
Print untuk menghasilkan laporan PDF.
Report untuk memuat data laporan.
3. Fitur Utama

a. Fungsi Pencarian Data Mahasiswa
Fungsi database() mengambil data dari dictionary lokal yang berisi NIM dan nama mahasiswa. Jika data ditemukan, nama lengkap dan akun email Unesa otomatis diisi pada form.

b. Pengambilan Gambar dengan Kamera
Fungsi mulai1() membuka jendela kamera untuk menangkap foto pengguna. OpenCV menangkap frame gambar dari kamera dan menampilkannya di antarmuka.

c. Deteksi Lokasi Berdasarkan IP
Aplikasi menggunakan geopy dan geocoder untuk mendeteksi lokasi pengguna berdasarkan alamat IP. Lokasi akan ditampilkan bersama data presensi.

d. Menyimpan Data dalam Format Excel
Data presensi, seperti NIM, nama, akun Unesa, dan mata kuliah yang dipilih, disimpan dalam file data.xlsx. Fungsi ini memastikan bahwa data terstruktur dan bisa diakses kembali.

e. Mencetak Laporan PDF
Aplikasi menggunakan FPDF untuk mencetak laporan PDF yang diambil dari data presensi. Hal ini memudahkan pengguna untuk mencetak bukti kehadiran.

4. Cara Menggunakan

Buka Aplikasi: Jalankan aplikasi dengan menjalankan file utama.
Isi Formulir Presensi: Masukkan NIM, nama, akun Unesa, dan mata kuliah. Pilih mata kuliah yang sesuai dengan hari tersebut.
Ambil Foto: Klik Camera 📷 untuk menangkap foto sebagai bukti presensi.
Simpan Data: Klik Submit untuk menyimpan data presensi ke file Excel.
Cetak Laporan PDF: Gunakan tombol Print untuk menghasilkan file PDF dari data presensi.
5. Struktur Folder

data.xlsx: File ini menyimpan data presensi dalam format Excel.
db/: Folder ini menyimpan database lokal yang diperlukan untuk foto pengguna.
profile.png, UNESA.png: Gambar yang digunakan sebagai ikon dan placeholder.

