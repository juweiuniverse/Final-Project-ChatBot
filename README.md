# Final-Project-ChatBot

*What are you making?*
Sistem rekomendasi lagu berbasis Large Language Model (LLM), CrewAI multi-agent, dan FAISS vector search.
Proyek ini memungkinkan pengguna menanyakan lagu berdasarkan karakteristik audio seperti danceability, energy, tempo, dan valence.

## Project Overview
Moodify bertujuan menghasilkan rekomendasi lagu yang relevan dengan preferensi pengguna. Projek ini memiliki kelemahan, yaitu hanya bisa menginputkan karakteristik audio (danceability, energy, valence, tempo, loudness, instrumentalness, dll.) saja, itupun harus benar-benar mengacu kepada kata-kata tersebut karena pada proyek ini belum dijeaskan untuk mood, seperti "relaksasi, happy, dll".
Model bekerja melalui tiga komponen utama:
1. FAISS Vectorstore
Menyimpan embedding seluruh dataset lagu. Dipakai untuk melakukan semantic search berdasarkan query.
2. CrewAI Multi-Agent
Song Researcher: Mengambil data dari FAISS. 
Recommendation Synthesizer: Merangkum hasil menjadi rekomendasi.
3. LLM (HuggingFace: Llama 3.1 8B)
Digunakan untuk memahami pertanyaan pengguna dan menyusun jawaban.

## Dataset

Dataset lagu yang digunakan tidak di-upload ke repository ini, namun hanya digunakan di Google Colab.

Sumber Dataset
Dataset diambil dari repository publik:

[https://github.com/orzanai/Moodify/blob/main/Datasets/1200_song_mapped.csv]

Lisensi Dataset
Dataset tersebut menggunakan lisensi sebagaimana tertera pada repository sumber.
Dataset tidak didistribusikan ulang dalam proyek ini dan hanya digunakan untuk tujuan akademik/demonstrasi.
Karena file CSV tidak disertakan di repo GitHub ini, proyek ini hanya menyediakan:
1. Kode pemrosesan
2. Notebook Colab untuk menjalankan sistem
3. Instruksi untuk mengunduh dataset dari sumber aslinya

## Design Choices
1. FAISS Vector Store
Dipilih karena:
a. Efisien untuk pencarian berbasis embedding
b. Mendukung query teks bebas
c. Dapat bekerja dengan dataset berukuran besar

2. Retriever Tool
Dibuat khusus untuk menerima query dalam bentuk dictionary, lalu melakukan pencarian data lagu yang relevan di vectorstore.

3. CrewAI Agents
Struktur agent digunakan untuk memisahkan tugas:
a. Researcher → mengambil data dari vectorstore
b. Synthesizer → merangkum dan menyusun rekomendasi ke format yang mudah dipahami
Pendekatan ini membuat chatbot modular dan mudah dikembangkan.

4. HuggingFace Inference API
Dipilih karena:
a. Mudah digunakan di Colab
b. Mendukung model open-source
c. API key dapat disimpan sebagai Colab Secret agar tidak muncul di kode

## How to Run the Project
1. Buka Notebook di Google Colab
2. Masukkan API Key ke Colab Secrets
3. Download Dataset dari Sumber Asli
4. Install Libraries
5. Load & Siapkan Dataset
6. Lakukan embedding
7. Siapkan LLM & Custom Tool
8. Definisikan Agent
9. Jalankan Chatbot
