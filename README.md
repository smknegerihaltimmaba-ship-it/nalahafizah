<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SMK Negeri 1 Halmahera Timur - Portal Resmi</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Alpine.js CDN -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
    <!-- FontAwesome untuk ikon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body class="bg-gray-50 text-gray-800 font-sans antialiased" x-data="schoolApp()">

    <!-- ==================== HEADER / NAVBAR ==================== -->
    <header class="bg-blue-900 text-white shadow-md sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-20 items-center">
                <!-- Logo & Identitas -->
                <div class="flex items-center space-x-3">
                    <div class="bg-white p-2 rounded-lg text-blue-900 font-bold text-xl shadow">
                        <i class="fa-solid fa-graduation-cap"></i>
                    </div>
                    <div>
                        <span class="text-xs uppercase tracking-wider text-blue-200 block">Official Portal</span>
                        <h1 class="text-lg font-bold leading-tight">SMK Negeri 1 Halmahera Timur</h1>
                    </div>
                </div>

                <!-- Navigasi Menu Public -->
                <nav class="hidden md:flex space-x-6 items-center font-medium">
                    <a href="#beranda" class="hover:text-blue-300 transition">Beranda</a>
                    <a href="#profil" class="hover:text-blue-300 transition">Profil & Jurusan</a>
                    <a href="#pengumuman" class="hover:text-blue-300 transition">Pengumuman</a>
                    <a href="#ppdb" class="hover:text-blue-300 transition">PPDB Online</a>
                    
                    <!-- Tombol Akses Login Admin -->
                    <button @click="openLoginModal = true" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg text-sm shadow transition flex items-center space-x-2">
                        <i class="fa-solid fa-lock"></i>
                        <span x-text="isAdminLoggedIn ? 'Dashboard Admin' : 'Login Admin'"></span>
                    </button>
                </nav>

                <!-- Mobile Menu Button -->
                <div class="md:hidden flex items-center space-x-2">
                    <button @click="openLoginModal = true" class="bg-blue-600 px-3 py-1.5 rounded text-xs">
                        <i class="fa-solid fa-lock"></i> Admin
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- ==================== MAIN CONTENT (PUBLIC) ==================== -->
    <main x-show="!isAdminLoggedIn || currentView === 'public'" x-transition>

        <!-- HERO SECTION -->
        <section id="beranda" class="bg-gradient-to-r from-blue-900 via-blue-800 to-indigo-900 text-white py-20 px-4">
            <div class="max-w-5xl mx-auto text-center space-y-6">
                <span class="bg-blue-700 text-blue-200 text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-wider">Unggul, Berkarakter & Kompeten</span>
                <h2 class="text-4xl md:text-5xl font-extrabold tracking-tight">Selamat Datang di SMK Negeri 1 Halmahera Timur</h2>
                <p class="text-lg text-blue-100 max-w-2xl mx-auto">Pusat pendidikan kejuruan terdepan di Maluku Utara yang mencetak lulusan siap kerja, mandiri, dan berdaya saing global.</p>
                <div class="flex justify-center space-x-4 pt-4">
                    <a href="#ppdb" class="bg-amber-500 hover:bg-amber-600 text-blue-950 font-bold px-6 py-3 rounded-lg shadow-lg transition">Daftar PPDB Online</a>
                    <a href="#profil" class="bg-white/10 hover:bg-white/20 text-white font-semibold px-6 py-3 rounded-lg backdrop-blur transition border border-white/20">Jelajahi Jurusan</a>
                </div>
            </div>
        </section>

        <!-- PROFIL & KONSENTRASI KEAHLIAN -->
        <section id="profil" class="py-16 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-12">
                <h3 class="text-3xl font-bold text-gray-900">Konsentrasi Keahlian (Jurusan)</h3>
                <p class="text-gray-600 mt-2">Pilihan program keahlian terbaik yang disesuaikan dengan kebutuhan dunia industri.</p>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-6 rounded-xl shadow border border-gray-100 hover:shadow-md transition">
                    <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-lg flex items-center justify-center text-xl mb-4"><i class="fa-solid fa-laptop-code"></i></div>
                    <h4 class="text-xl font-bold mb-2">Teknik Komputer & Jaringan</h4>
                    <p class="text-gray-600 text-sm">Mempelajari perakitan komputer, administrasi jaringan server, mikrotik, fiber optic, dan keamanan siber.</p>
                </div>
                <div class="bg-white p-6 rounded-xl shadow border border-gray-100 hover:shadow-md transition">
                    <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-lg flex items-center justify-center text-xl mb-4"><i class="fa-solid fa-car"></i></div>
                    <h4 class="text-xl font-bold mb-2">Teknik Kendaraan Ringan</h4>
                    <p class="text-gray-600 text-sm">Fokus pada perbaikan, perawatan, dan diagnosa mesin otomotif modern roda empat serta teknologi kelistrikan kendaraan.</p>
                </div>
                <div class="bg-white p-6 rounded-xl shadow border border-gray-100 hover:shadow-md transition">
                    <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-lg flex items-center justify-center text-xl mb-4"><i class="fa-solid fa-calculator"></i></div>
                    <h4 class="text-xl font-bold mb-2">Akuntansi & Keuangan Lembaga</h4>
                    <p class="text-gray-600 text-sm">Menguasai siklus akuntansi perusahaan jasa, dagang, manufaktur, perpajakan, serta aplikasi komputer akuntansi.</p>
                </div>
            </div>
        </section>

        <!-- PENGUMUMAN PUBLIK -->
        <section id="pengumuman" class="py-16 bg-gray-100 px-4 sm:px-6 lg:px-8">
            <div class="max-w-5xl mx-auto">
                <div class="text-center mb-10">
                    <h3 class="text-3xl font-bold text-gray-900">Pengumuman Terbaru</h3>
                    <p class="text-gray-600 mt-1">Informasi resmi seputar kegiatan akademik dan sekolah.</p>
                </div>
                <div class="space-y-4">
                    <template x-for="item in announcements" :key="item.id">
                        <div class="bg-white p-6 rounded-lg shadow-sm border-l-4 border-blue-600">
                            <div class="flex justify-between items-center mb-2">
                                <span class="text-xs font-semibold text-blue-600 bg-blue-50 px-2.5 py-1 rounded" x-text="item.tanggal"></span>
                            </div>
                            <h4 class="text-lg font-bold text-gray-800" x-text="item.judul"></h4>
                            <p class="text-gray-600 text-sm mt-1" x-text="item.isi"></p>
                        </div>
                    </template>
                </div>
            </div>
        </section>

        <!-- FORM PPDB ONLINE -->
        <section id="ppdb" class="py-16 max-w-4xl mx-auto px-4">
            <div class="bg-white rounded-2xl shadow-lg border border-gray-100 p-8">
                <div class="text-center mb-8">
                    <h3 class="text-2xl font-bold text-gray-900">Formulir Pendaftaran Siswa Baru (PPDB)</h3>
                    <p class="text-gray-600 text-sm mt-1">Silakan lengkapi data diri Anda dengan benar untuk mendaftar.</p>
                </div>

                <form @submit.prevent="submitPPDB" class="space-y-4">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">Nama Lengkap</label>
                            <input type="text" x-model="formPPDB.nama" required class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none text-sm">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">NISN</label>
                            <input type="text" x-model="formPPDB.nisn" required class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none text-sm">
                        </div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">Asal Sekolah (SMP/MTs)</label>
                            <input type="text" x-model="formPPDB.asalSekolah" required class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none text-sm">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">Pilihan Konsentrasi Keahlian</label>
                            <select x-model="formPPDB.jurusan" required class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none text-sm bg-white">
                                <option value="">-- Pilih Jurusan --</option>
                                <option value="Teknik Komputer & Jaringan">Teknik Komputer & Jaringan</option>
                                <option value="Teknik Kendaraan Ringan">Teknik Kendaraan Ringan</option>
                                <option value="Akuntansi & Keuangan Lembaga">Akuntansi & Keuangan Lembaga</option>
                            </select>
                        </div>
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Nomor WhatsApp Aktif</label>
                        <input type="text" x-model="formPPDB.whatsapp" required class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none text-sm" placeholder="Contoh: 081234567890">
                    </div>
                    <div class="pt-4 text-center">
                        <button type="submit" class="w-full md:w-auto bg-blue-600 hover:bg-blue-700 text-white font-medium px-8 py-3 rounded-lg shadow transition">Kirim Pendaftaran</button>
                    </div>
                </form>
            </div>
        </section>
    </main>

    <!-- ==================== ADMIN PORTAL / DASHBOARD (HANYA ADMIN) ==================== -->
    <div x-show="isAdminLoggedIn && currentView === 'admin'" class="min-h-screen bg-gray-100 flex" x-transition>
        <!-- Sidebar Admin -->
        <aside class="w-64 bg-blue-950 text-white flex flex-col justify-between hidden md:flex">
            <div>
                <div class="p-6 border-b border-blue-900">
                    <span class="text-xs text-blue-400 uppercase tracking-widest">Panel Kontrol</span>
                    <h2 class="text-lg font-bold mt-1">Admin SMK N 1 Haltim</h2>
                </div>
                <nav class="p-4 space-y-2">
                    <button @click="adminTab = 'ppdb'" :class="adminTab === 'ppdb' ? 'bg-blue-800 text-white' : 'text-blue-300 hover:bg-blue-900 hover:text-white'" class="w-full text-left px-4 py-2.5 rounded-lg text-sm font-medium transition flex items-center space-x-3">
                        <i class="fa-solid fa-users-line"></i> <span>Data PPDB Masuk</span>
                    </button>
                    <button @click="adminTab = 'announcement'" :class="adminTab === 'announcement' ? 'bg-blue-800 text-white' : 'text-blue-300 hover:bg-blue-900 hover:text-white'" class="w-full text-left px-4 py-2.5 rounded-lg text-sm font-medium transition flex items-center space-x-3">
                        <i class="fa-solid fa-bullhorn"></i> <span>Kelola Pengumuman</span>
                    </button>
                </nav>
            </div>
            <div class="p-4 border-t border-blue-900">
                <button @click="logoutAdmin" class="w-full bg-red-600 hover:bg-red-700 text-white px-4 py-2 rounded-lg text-sm transition flex items-center justify-center space-x-2">
                    <i class="fa-solid fa-right-from-bracket"></i> <span>Keluar Admin</span>
                </button>
            </div>
        </aside>

        <!-- Main Admin Area -->
        <div class="flex-1 flex flex-col min-h-screen">
            <!-- Topbar Admin -->
            <header class="bg-white shadow-sm h-16 flex items-center justify-between px-6">
                <div class="flex items-center space-x-4">
                    <button @click="currentView = 'public'" class="bg-gray-100 hover:bg-gray-200 text-gray-700 px-3 py-1.5 rounded text-xs font-medium transition">
                        <i class="fa-solid fa-globe"></i> Lihat Website Publik
                    </button>
                    <span class="text-sm font-semibold text-gray-700">Mode Administrator Aktif</span>
                </div>
                <button @click="logoutAdmin" class="md:hidden text-red-600 text-sm font-medium">Keluar</button>
            </header>

            <!-- Content Area Admin -->
            <main class="p-6 flex-1 overflow-y-auto">

                <!-- TAB 1: DATA PPDB -->
                <div x-show="adminTab === 'ppdb'">
                    <div class="flex justify-between items-center mb-6">
                        <div>
                            <h3 class="text-2xl font-bold text-gray-900">Kelola Data Pendaftar PPDB</h3>
                            <p class="text-sm text-gray-600">Edit manual, ubah status, atau hapus data pendaftar siswa baru.</p>
                        </div>
                        <button @click="openAddPpdbModal()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg text-sm font-medium shadow transition">
                            <i class="fa-solid fa-plus mr-1"></i> Tambah Data Manual
                        </button>
                    </div>

                    <!-- Tabel PPDB -->
                    <div class="bg-white rounded-xl shadow overflow-hidden border border-gray-200">
                        <table class="w-full text-left border-collapse text-sm">
                            <thead class="bg-gray-50 text-gray-700 uppercase tracking-wider text-xs border-b">
                                <tr>
                                    <th class="p-4">Nama Lengkap</th>
                                    <th class="p-4">NISN</th>
                                    <th class="p-4">Asal Sekolah</th>
                                    <th class="p-4">Jurusan</th>
                                    <th class="p-4">WhatsApp</th>
                                    <th class="p-4 text-center">Aksi (Edit/Hapus)</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-gray-200">
                                <template x-for="(student, index) in registrants" :key="student.id">
                                    <tr class="hover:bg-gray-50">
                                        <td class="p-4 font-semibold text-gray-900" x-text="student.nama"></td>
                                        <td class="p-4 text-gray-600" x-text="student.nisn"></td>
                                        <td class="p-4 text-gray-600" x-text="student.asalSekolah"></td>
                                        <td class="p-4"><span class="bg-blue-50 text-blue-700 text-xs px-2.5 py-1 rounded font-medium" x-text="student.jurusan"></span></td>
                                        <td class="p-4 text-gray-600" x-text="student.whatsapp"></td>
                                        <td class="p-4 text-center space-x-2">
                                            <button @click="editPpdb(index)" class="text-blue-600 hover:text-blue-800 p-1" title="Edit Manual"><i class="fa-solid fa-pen-to-square"></i></button>
                                            <button @click="deletePpdb(index)" class="text-red-600 hover:text-red-800 p-1" title="Hapus"><i class="fa-solid fa-trash"></i></button>
                                        </td>
                                    </tr>
                                </template>
                                <template x-if="registrants.length === 0">
                                    <tr>
                                        <td colspan="6" class="p-6 text-center text-gray-500">Belum ada data pendaftar PPDB.</td>
                                    </tr>
                                </template>
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- TAB 2: KELOLA PENGUMUMAN -->
                <div x-show="adminTab === 'announcement'">
                    <div class="flex justify-between items-center mb-6">
                        <div>
                            <h3 class="text-2xl font-bold text-gray-900">Kelola Pengumuman Sekolah</h3>
                            <p class="text-sm text-gray-600">Tambah atau edit informasi pengumuman publik.</p>
                        </div>
                        <button @click="openAddAnnouncementModal()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg text-sm font-medium shadow transition">
                            <i class="fa-solid fa-plus mr-1"></i> Buat Pengumuman Baru
                        </button>
                    </div>

                    <!-- Tabel Pengumuman -->
                    <div class="bg-white rounded-xl shadow overflow-hidden border border-gray-200">
                        <table class="w-full text-left border-collapse text-sm">
                            <thead class="bg-gray-50 text-gray-700 uppercase tracking-wider text-xs border-b">
                                <tr>
                                    <th class="p-4">Tanggal</th>
                                    <th class="p-4">Judul Pengumuman</th>
                                    <th class="p-4">Isi Informasi</th>
                                    <th class="p-4 text-center">Aksi</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-gray-200">
                                <template x-for="(ann, index) in announcements" :key="ann.id">
                                    <tr class="hover:bg-gray-50">
                                        <td class="p-4 text-xs font-semibold text-blue-600" x-text="ann.tanggal"></td>
                                        <td class="p-4 font-semibold text-gray-900" x-text="ann.judul"></td>
                                        <td class="p-4 text-gray-600 text-xs truncate max-w-xs" x-text="ann.isi"></td>
                                        <td class="p-4 text-center space-x-2">
                                            <button @click="editAnnouncement(index)" class="text-blue-600 hover:text-blue-800 p-1"><i class="fa-solid fa-pen-to-square"></i></button>
                                            <button @click="deleteAnnouncement(index)" class="text-red-600 hover:text-red-800 p-1"><i class="fa-solid fa-trash"></i></button>
                                        </td>
                                    </tr>
                                </template>
                            </tbody>
                        </table>
                    </div>
                </div>

            </main>
        </div>
    </div>

    <!-- ==================== MODAL LOGIN ADMIN ==================== -->
    <div x-show="openLoginModal" class="fixed inset-0 bg-black/50 backdrop-blur-sm flex items-center justify-center z-50 p-4" x-transition>
        <div class="bg-white rounded-2xl shadow-xl max-w-sm w-full p-6 relative">
            <button @click="openLoginModal = false" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            <div class="text-center mb-6">
                <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-full flex items-center justify-center mx-auto mb-2 text-lg"><i class="fa-solid fa-shield-halved"></i></div>
                <h3 class="text-xl font-bold text-gray-900">Login Administrator</h3>
                <p class="text-xs text-gray-500 mt-1">Masukkan kredensial khusus pengelola web.</p>
            </div>
            
            <form @submit.prevent="handleLogin" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold uppercase text-gray-600 mb-1">Username</label>
                    <input type="text" x-model="loginForm.username" required class="w-full px-3 py-2 border rounded-lg text-sm focus:ring-2 focus:ring-blue-500 focus:outline-none" placeholder="adminhaltim">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-gray-600 mb-1">Password</label>
                    <input type="password" x-model="loginForm.password" required class="w-full px-3 py-2 border rounded-lg text-sm focus:ring-2 focus:ring-blue-500 focus:outline-none" placeholder="••••••••">
                </div>
                <p x-show="loginError" class="text-xs text-red-600 text-center font-medium">Username atau Password salah! (Gunakan: admin / smkn1haltim)</p>
                <button type="submit" class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2.5 rounded-lg text-sm font-medium shadow transition">Masuk Panel Admin</button>
            </form>
        </div>
    </div>

    <!-- ==================== MODAL EDIT / TAMBAH MANUAL PPDB ==================== -->
    <div x-show="showPpdbModal" class="fixed inset-0 bg-black/50 backdrop-blur-sm flex items-center justify-center z-50 p-4" x-transition>
        <div class="bg-white rounded-2xl shadow-xl max-w-lg w-full p-6 relative">
            <button @click="showPpdbModal = false" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            <h3 class="text-lg font-bold text-gray-900 mb-4" x-text="editPpdbIndex === null ? 'Tambah Data PPDB Manual' : 'Edit Data PPDB'"></h3>
            
            <form @submit.prevent="savePpdbManual" class="space-y-3">
                <div>
                    <label class="block text-xs font-medium text-gray-700 mb-1">Nama Lengkap</label>
                    <input type="text" x-model="modalPpdbData.nama" required class="w-full px-3 py-2 border rounded-lg text-sm">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-medium text-gray-700 mb-1">NISN</label>
                        <input type="text" x-model="modalPpdbData.nisn" required class="w-full px-3 py-2 border rounded-lg text-sm">
                    </div>
                    <div>
                        <label class="block text-xs font-medium text-gray-700 mb-1">WhatsApp</label>
                        <input type="text" x-model="modalPpdbData.whatsapp" required class="w-full px-3 py-2 border rounded-lg text-sm">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-medium text-gray-700 mb-1">Asal Sekolah</label>
                    <input type="text" x-model="modalPpdbData.asalSekolah" required class="w-full px-3 py-2 border rounded-lg text-sm">
                </div>
                <div>
                    <label class="block text-xs font-medium text-gray-700 mb-1">Konsentrasi Keahlian</label>
                    <select x-model="modalPpdbData.jurusan" required class="w-full px-3 py-2 border rounded-lg text-sm bg-white">
                        <option value="Teknik Komputer & Jaringan">Teknik Komputer & Jaringan</option>
                        <option value="Teknik Kendaraan Ringan">Teknik Kendaraan Ringan</option>
                        <option value="Akuntansi & Keuangan Lembaga">Akuntansi & Keuangan Lembaga</option>
                    </select>
                </div>
                <div class="pt-4 flex justify-end space-x-2">
                    <button type="button" @click="showPpdbModal = false" class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg text-sm">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-blue-600 text-white rounded-lg text-sm font-medium">Simpan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- ==================== MODAL EDIT / TAMBAH PENGUMUMAN ==================== -->
    <div x-show="showAnnModal" class="fixed inset-0 bg-black/50 backdrop-blur-sm flex items-center justify-center z-50 p-4" x-transition>
        <div class="bg-white rounded-2xl shadow-xl max-w-lg w-full p-6 relative">
            <button @click="showAnnModal = false" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            <h3 class="text-lg font-bold text-gray-900 mb-4" x-text="editAnnIndex === null ? 'Tambah Pengumuman Baru' : 'Edit Pengumuman'"></h3>
            
            <form @submit.prevent="saveAnnouncementManual" class="space-y-3">
                <div>
                    <label class="block text-xs font-medium text-gray-700 mb-1">Tanggal</label>
                    <input type="text" x-model="modalAnnData.tanggal" required class="w-full px-3 py-2 border rounded-lg text-sm" placeholder="Contoh: 10 November 2026">
                </div>
                <div>
                    <label class="block text-xs font-medium text-gray-700 mb-1">Judul Pengumuman</label>
                    <input type="text" x-model="modalAnnData.judul" required class="w-full px-3 py-2 border rounded-lg text-sm">
                </div>
                <div>
                    <label class="block text-xs font-medium text-gray-700 mb-1">Isi Informasi Lengkap</label>
                    <textarea x-model="modalAnnData.isi" rows="4" required class="w-full px-3 py-2 border rounded-lg text-sm"></textarea>
                </div>
                <div class="pt-4 flex justify-end space-x-2">
                    <button type="button" @click="showAnnModal = false" class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg text-sm">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-blue-600 text-white rounded-lg text-sm font-medium">Simpan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- ==================== LOGIC JAVASCRIPT (ALPINE.JS) ==================== -->
    <script>
        function schoolApp() {
            return {
                isAdminLoggedIn: localStorage.getItem('admin_logged_in') === 'true',
                currentView: 'public', // 'public' atau 'admin'
                adminTab: 'ppdb',
                openLoginModal: false,
                loginError: false,
                loginForm: { username: '', password: '' },

                // Data Pengumuman (tersimpan di localStorage)
                announcements: JSON.parse(localStorage.getItem('smk_announcements')) || [
                    { id: 1, tanggal: '08 November 2026', judul: 'Jadwal Simulasi Ujian Kompetensi Keahlian (UKK)', isi: 'Seluruh siswa kelas XII diimbau untuk mempersiapkan diri mengikuti simulasi UKK mulai hari Senin mendatang.' },
                    { id: 2, tanggal: '01 November 2026', judul: 'Pembukaan Pendaftaran PPDB Tahun Ajaran 2026/2027', isi: 'Pendaftaran Peserta Didik Baru SMK Negeri 1 Halmahera Timur resmi dibuka secara online melalui portal ini.' }
                ],

                // Data Pendaftar PPDB (tersimpan di localStorage)
                registrants: JSON.parse(localStorage.getItem('smk_registrants')) || [
                    { id: 1, nama: 'Ahmad Fikri', nisn: '0081234567', asalSekolah: 'SMPN 1 Maba', jurusan: 'Teknik Komputer & Jaringan', whatsapp: '081234567891' },
                    { id: 2, nama: 'Siti Rahma', nisn: '0089876543', asalSekolah: 'MTs Negeri 1 Haltim', jurusan: 'Akuntansi & Keuangan Lembaga', whatsapp: '081298765432' }
                ],

                // Form State Public PPDB
                formPPDB: { nama: '', nisn: '', asalSekolah: '', jurusan: '', whatsapp: '' },

                // Modal States Admin
                showPpdbModal: false,
                editPpdbIndex: null,
                modalPpdbData: { nama: '', nisn: '', asalSekolah: '', jurusan: '', whatsapp: '' },

                showAnnModal: false,
                editAnnIndex: null,
                modalAnnData: { tanggal: '', judul: '', isi: '' },

                // Login Handler
                handleLogin() {
                    // Kredensial Admin Default
                    if (this.loginForm.username === 'admin' && this.loginForm.password === 'smkn1haltim') {
                        this.isAdminLoggedIn = true;
                        this.currentView = 'admin';
                        this.openLoginModal = false;
                        this.loginError = false;
                        localStorage.setItem('admin_logged_in', 'true');
                        this.loginForm.username = '';
                        this.loginForm.password = '';
                    } else {
                        this.loginError = true;
                    }
                },

                logoutAdmin() {
                    this.isAdminLoggedIn = false;
                    this.currentView = 'public';
                    localStorage.removeItem('admin_logged_in');
                },

                // Submit Form PPDB dari Publik
                submitPPDB() {
                    const newEntry = {
                        id: Date.now(),
                        ...this.formPPDB
                    };
                    this.registrants.unshift(newEntry);
                    localStorage.setItem('smk_registrants', JSON.stringify(this.registrants));
                    alert('Pendaftaran PPDB Berhasil dikirim! Data Anda telah tercatat di sistem sekolah.');
                    this.formPPDB = { nama: '', nisn: '', asalSekolah: '', jurusan: '', whatsapp: '' };
                },

                // CRUD PPDB (Admin)
                openAddPpdbModal() {
                    this.editPpdbIndex = null;
                    this.modalPpdbData = { nama: '', nisn: '', asalSekolah: '', jurusan: '', whatsapp: '' };
                    this.showPpdbModal = true;
                },
                editPpdb(index) {
                    this.editPpdbIndex = index;
                    this.modalPpdbData = { ...this.registrants[index] };
                    this.showPpdbModal = true;
                },
                savePpdbManual() {
                    if (this.editPpdbIndex === null) {
                        this.registrants.unshift({ id: Date.now(), ...this.modalPpdbData });
                    } else {
                        this.registrants[this.editPpdbIndex] = { ...this.registrants[this.editPpdbIndex], ...this.modalPpdbData };
                    }
                    localStorage.setItem('smk_registrants', JSON.stringify(this.registrants));
                    this.showPpdbModal = false;
                },
                deletePpdb(index) {
                    if (confirm('Yakin ingin menghapus data pendaftar ini?')) {
                        this.registrants.splice(index, 1);
                        localStorage.setItem('smk_registrants', JSON.stringify(this.registrants));
                    }
                },

                // CRUD Pengumuman (Admin)
                openAddAnnouncementModal() {
                    this.editAnnIndex = null;
                    this.modalAnnData = { tanggal: '', judul: '', isi: '' };
                    this.showAnnModal = true;
                },
                editAnnouncement(index) {
                    this.editAnnIndex = index;
                    this.modalAnnData = { ...this.announcements[index] };
                    this.showAnnModal = true;
                },
                saveAnnouncementManual() {
                    if (this.editAnnIndex === null) {
                        this.announcements.unshift({ id: Date.now(), ...this.modalAnnData });
                    } else {
                        this.announcements[this.editAnnIndex] = { ...this.announcements[this.editAnnIndex], ...this.modalAnnData };
                    }
                    localStorage.setItem('smk_announcements', JSON.stringify(this.announcements));
                    this.showAnnModal = false;
                },
                deleteAnnouncement(index) {
                    if (confirm('Yakin ingin menghapus pengumuman ini?')) {
                        this.announcements.splice(index, 1);
                        localStorage.setItem('smk_announcements', JSON.stringify(this.announcements));
                    }
                }
            }
        }
    </script>
</body>
</html>
