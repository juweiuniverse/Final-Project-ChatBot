# Final-Project-ChatBot

*What are you making?*
Sistem rekomendasi lagu berbasis Large Language Model (LLM), CrewAI multi-agent, dan FAISS vector search.
Proyek ini memungkinkan pengguna menanyakan lagu berdasarkan karakteristik audio seperti danceability, energy, tempo, dan valence.

1. Project Overview
Moodify bertujuan menghasilkan rekomendasi lagu yang relevan dengan preferensi pengguna. Projek ini memiliki kelemahan, yaitu hanya bisa menginputkan karakteristik audio (danceability, energy, valence, tempo, loudness, instrumentalness, dll.) saja, itupun harus benar-benar mengacu kepada kata-kata tersebut karena pada proyek ini belum dijeaskan untuk mood, seperti "relaksasi, happy, dll".
Model bekerja melalui tiga komponen utama:
a. FAISS Vectorstore
Menyimpan embedding seluruh dataset lagu. Dipakai untuk melakukan semantic search berdasarkan query.
b. CrewAI Multi-Agent
Song Researcher: Mengambil data dari FAISS. 
Recommendation Synthesizer: Merangkum hasil menjadi rekomendasi.
c. LLM (HuggingFace: Llama 3.1 8B)
Digunakan untuk memahami pertanyaan pengguna dan menyusun jawaban.

2. Dataset

Dataset lagu yang digunakan tidak di-upload ke repository ini, namun hanya digunakan di Google Colab.

Sumber Dataset
Dataset diambil dari repository publik:

[https://github.com/orzanai/Moodify/blob/main/Datasets/1200_song_mapped.csv]

Lisensi Dataset
Dataset tersebut menggunakan lisensi sebagaimana tertera pada repository sumber.
Dataset tidak didistribusikan ulang dalam proyek ini dan hanya digunakan untuk tujuan akademik/demonstrasi.
Karena file CSV tidak disertakan di repo GitHub ini, proyek ini hanya menyediakan:
a. Kode pemrosesan
b. Notebook Colab untuk menjalankan sistem
c. Instruksi untuk mengunduh dataset dari sumber aslinya

3. Design Choices
a. FAISS Vector Store
Dipilih karena:
1) Efisien untuk pencarian berbasis embedding
2)  Mendukung query teks bebas
3) Dapat bekerja dengan dataset berukuran besar

b. Retriever Tool
Dibuat khusus untuk menerima query dalam bentuk dictionary, lalu melakukan pencarian data lagu yang relevan di vectorstore.

c. CrewAI Agents
Struktur agent digunakan untuk memisahkan tugas:
1) Researcher → mengambil data dari vectorstore
2) Synthesizer → merangkum dan menyusun rekomendasi ke format yang mudah dipahami
Pendekatan ini membuat chatbot modular dan mudah dikembangkan.

d. HuggingFace Inference API
Dipilih karena:
1) Mudah digunakan di Colab
2) Mendukung model open-source
3) API key dapat disimpan sebagai Colab Secret agar tidak muncul di kode

4. How to Run the Project
Step 1 — Buka Notebook di Google Colab
Step 2 — Masukkan API Key ke Colab Secrets
Step 3 — Download Dataset dari Sumber Asli
Step 4 — Install Libraries
Step 5 — Load & Siapkan Dataset
Step 6 — Lakukan embedding
Step 7 — Siapkan LLM & Custom Tool
Step 8 — Definisikan Agent
Step 9 — Jalankan Chatbot
