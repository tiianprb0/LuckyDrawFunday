<?php
// Ganti dengan password yang aman
const ADMIN_PASSWORD = "tiian";
const PARTICIPANTS_FILE = 'participants.json';

// Fungsi untuk membaca data dari berkas JSON
function readParticipants() {
    if (!file_exists(PARTICIPANTS_FILE)) {
        return ['participants' => []];
    }
    $json = file_get_contents(PARTICIPANTS_FILE);
    $data = json_decode($json, true);
    if (!isset($data['participants']) || !is_array($data['participants'])) {
        $data = ['participants' => []];
    }
    return $data;
}

// Fungsi untuk menulis data ke berkas JSON
function writeParticipants($data) {
    file_put_contents(PARTICIPANTS_FILE, json_encode($data, JSON_PRETTY_PRINT));
}

// Menangani permintaan POST dari formulir
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['password']) && $_POST['password'] === ADMIN_PASSWORD) {
    if (isset($_POST['action'])) {
        $action = $_POST['action'];
        $data = readParticipants();
        $response = ['success' => false, 'message' => ''];

        if ($action === 'add') {
            $names = explode("\n", $_POST['names']);
            $names = array_map('trim', $names);
            $names = array_filter($names);

            $addedCount = 0;
            foreach ($names as $name) {
                $isDuplicate = false;
                foreach ($data['participants'] as $participant) {
                    if ($participant['name'] === $name) {
                        $isDuplicate = true;
                        break;
                    }
                }
                if (!$isDuplicate) {
                    $data['participants'][] = ['id' => uniqid(), 'name' => $name, 'hasWon' => false, 'isGrandWinner' => false];
                    $addedCount++;
                }
            }
            writeParticipants($data);
            $response = ['success' => true, 'message' => "Berhasil menambahkan {$addedCount} peserta."];
        }

        if ($action === 'delete') {
            $id = $_POST['id'];
            $initialCount = count($data['participants']);
            $data['participants'] = array_filter($data['participants'], function ($p) use ($id) {
                return $p['id'] !== $id;
            });
            $data['participants'] = array_values($data['participants']);
            writeParticipants($data);
            $response = ['success' => (count($data['participants']) < $initialCount), 'message' => 'Peserta berhasil dihapus.'];
        }

        if ($action === 'reset') {
            $data['participants'] = array_map(function ($p) {
                $p['hasWon'] = false;
                $p['isGrandWinner'] = false;
                return $p;
            }, $data['participants']);
            writeParticipants($data);
            $response = ['success' => true, 'message' => 'Daftar pemenang berhasil di-reset.'];
        }
        
        header('Content-Type: application/json');
        echo json_encode($response);
        exit;
    }
}
?>
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Draw Admin</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&family=Playfair+Display:wght@700&family=Cormorant+Garamond:wght@300;400;700&family=Kaushan+Script&family=Italianno&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #D4AF37;
            --secondary: #B8860B;
            --dark: #4B4B4B;
            --light: #f8f8f8;
            --gray: #9E9E9E;
            --warm-light: #FAFAFA;
            --border: #E0E0E0;
            --body-bg: #F5F5F5;
            --card-bg: #FFFFFF;
            --red-error: #D32F2F;
            --green-success: #4CAF50;
        }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: var(--body-bg);
            color: var(--dark);
            padding: 20px;
            margin: 0;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background-color: var(--card-bg);
            padding: 2rem;
            border-radius: 1rem;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }

        h1, h2 {
            font-family: 'Playfair Display', serif;
            color: var(--primary);
            text-align: center;
        }
        
        h2 {
            margin-top: 2rem;
        }

        .input-group, .prize-item {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-bottom: 1rem;
            align-items: center;
        }
        
        .input-group > input {
            flex-grow: 1;
            min-width: 150px;
        }
        
        input[type="text"], input[type="number"], .password-input, textarea {
            padding: 0.75rem;
            border: 1px solid var(--border);
            border-radius: 0.5rem;
            font-size: 1rem;
            width: 100%;
            box-sizing: border-box;
        }
        
        .button {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: 0.5rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
        }

        .button-primary {
            background-color: var(--primary);
            color: white;
        }

        .button-primary:hover:not(:disabled) {
            background-color: var(--secondary);
            transform: translateY(-1px);
        }

        .button-danger {
            background-color: var(--red-error);
            color: white;
        }

        .button-danger:hover:not(:disabled) {
            opacity: 0.8;
        }

        .button-secondary {
            background-color: var(--gray);
            color: white;
        }
        
        .button-secondary:hover:not(:disabled) {
            background-color: #666;
        }

        .button:disabled {
            background-color: #e0e0e0;
            color: #a0a0a0;
            cursor: not-allowed;
        }

        .password-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            text-align: center;
        }

        .password-container h1 {
            margin-bottom: 1rem;
        }

        .admin-content {
            display: none;
        }
        
        .list-container {
            border: 1px solid var(--border);
            border-radius: 0.5rem;
            padding: 1rem;
            max-height: 400px;
            overflow-y: auto;
            margin-top: 1rem;
        }

        .list-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--border);
        }
        
        .list-item:last-child {
            border-bottom: none;
        }
        
        .prize-image-preview {
            width: 50px;
            height: 50px;
            object-fit: cover;
            border-radius: 0.25rem;
        }
        
        .message-box {
            background-color: var(--green-success);
            color: white;
            padding: 1rem;
            border-radius: 0.5rem;
            text-align: center;
            margin-bottom: 1rem;
            display: none;
        }
        
        .message-box.error {
            background-color: var(--red-error);
        }
        
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        .modal-content {
            background-color: white;
            padding: 2rem;
            border-radius: 1rem;
            text-align: center;
        }
        
        .modal-buttons {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-top: 1rem;
        }

        /* Styles for tabs */
        .tab-container {
            display: flex;
            justify-content: space-around;
            border-bottom: 2px solid var(--border);
            margin-bottom: 1.5rem;
        }

        .tab-button {
            background-color: transparent;
            border: none;
            padding: 1rem;
            font-size: 1.1rem;
            font-weight: 600;
            color: var(--gray);
            cursor: pointer;
            transition: color 0.3s, border-bottom 0.3s;
        }

        .tab-button.active {
            color: var(--primary);
            border-bottom: 3px solid var(--primary);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }
        
        .winner-list-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--border);
            position: relative;
        }

        .winner-list-item .delete-button {
            position: absolute;
            right: 0;
        }
    </style>
</head>
<body>

    <div id="passwordSection" class="password-container">
        <h1>Halaman Admin</h1>
        <p>Masukkan password untuk melanjutkan:</p>
        <div class="input-group" style="width: 300px;">
            <input type="password" id="passwordInput" class="password-input" placeholder="Password">
            <button id="loginButton" class="button button-primary">Masuk</button>
        </div>
        <div id="loginMessage" class="message-box mt-2"></div>
    </div>

    <div id="adminContent" class="admin-content container">
        <h1>Dashboard Admin</h1>
        <div id="adminMessage" class="message-box"></div>
        
        <!-- Tab Navigation -->
        <div class="tab-container">
            <button class="tab-button active" data-tab="participants">Peserta</button>
            <button class="tab-button" data-tab="regular-prizes">Hadiah Biasa</button>
            <button class="tab-button" data-tab="grand-prizes">Grand Lucky Draw</button>
            <button class="tab-button" data-tab="winners">Pemenang</button>
        </div>

        <!-- Tab Content -->
        <div id="participants-tab" class="tab-content active">
            <h2>Kelola Peserta</h2>
            <form id="addParticipantForm" style="display: flex; flex-direction: column; align-items: stretch; gap: 1rem;">
                <label for="participantNames" style="font-weight: 600;">Tambahkan Peserta (satu nama per baris):</label>
                <textarea id="participantNames" name="names" rows="5" placeholder="Masukkan nama-nama peserta di sini..."></textarea>
                <button type="submit" class="button button-primary">Tambah Peserta</button>
            </form>
            <div id="participantsList" class="list-container">
                <!-- Participants will be loaded here -->
            </div>
            <button id="resetParticipantsButton" class="button button-danger" style="width: 100%; margin-top: 1rem;">Reset Semua Peserta</button>
        </div>
        
        <div id="regular-prizes-tab" class="tab-content">
            <h2>Kelola Hadiah Undian Biasa</h2>
            <div class="input-group">
                <input type="text" id="prizeName" placeholder="Nama Hadiah">
                <input type="text" id="prizeImage" placeholder="URL Gambar Hadiah">
                <input type="number" id="prizeQuota" placeholder="Kuota">
                <button id="addPrizeButton" class="button button-primary">Tambah Hadiah</button>
            </div>
            <div id="regularPrizesList" class="list-container"></div>
        </div>

        <div id="grand-prizes-tab" class="tab-content">
            <h2>Kelola Hadiah Grand Lucky Draw</h2>
            <div class="input-group">
                <input type="text" id="grandPrizeName" placeholder="Nama Grand Prize">
                <input type="text" id="grandPrizeImage" placeholder="URL Gambar Grand Prize">
                <input type="number" id="grandPrizeRank" placeholder="Peringkat (1, 2, 3)">
                <button id="addGrandPrizeButton" class="button button-primary">Tambah Grand Prize</button>
            </div>
            <div id="grandPrizesList" class="list-container"></div>
        </div>

        <div id="winners-tab" class="tab-content">
            <h2>Pemenang Undian</h2>
            <p>Pemenang undian biasa:</p>
            <div id="regularWinnersList" class="list-container">
                <p style="text-align: center; color: var(--gray); font-style: italic;">Belum ada pemenang undian biasa.</p>
            </div>
            <p style="margin-top: 1rem;">Pemenang Grand Lucky Draw:</p>
            <div id="grandWinnersList" class="list-container">
                <p style="text-align: center; color: var(--gray); font-style: italic;">Belum ada pemenang Grand Lucky Draw.</p>
            </div>
        </div>
    </div>
    
    <!-- Modal untuk konfirmasi hapus pemenang -->
    <div id="deleteWinnerModal" class="modal">
        <div class="modal-content">
            <h3>Konfirmasi Hapus Pemenang</h3>
            <p>Anda yakin ingin menghapus pemenang ini? Nama mereka akan dikembalikan ke daftar undian.</p>
            <div class="modal-buttons">
                <button id="confirmDeleteButton" class="button button-danger">Hapus</button>
                <button id="cancelDeleteButton" class="button button-secondary">Batal</button>
            </div>
        </div>
    </div>
    
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/12.2.1/firebase-app.js";
        import { getFirestore, collection, getDocs, doc, setDoc, addDoc, deleteDoc, query, onSnapshot, where, writeBatch, getDoc } from "https://www.gstatic.com/firebasejs/12.2.1/firebase-firestore.js";
        import { getAuth, signInWithCustomToken, signInAnonymously } from "https://www.gstatic.com/firebasejs/12.2.1/firebase-auth.js";
        import { setLogLevel } from "https://www.gstatic.com/firebasejs/12.2.1/firebase-firestore.js";
        
        // Atur level log untuk melihat pesan debug dari Firestore
        setLogLevel('Debug');

        // Firebase Configuration
        const firebaseConfig = {
            apiKey: "AIzaSyA01Obl9mGwWUQe4wvFuSpKBWJC-SetWrE",
            authDomain: "funday-test-pls.firebaseapp.com",
            projectId: "funday-test-pls",
            storageBucket: "funday-test-pls.firebasestorage.app",
            messagingSenderId: "468514863657",
            appId: "1:468514863657:web:a1b381fa0f777c2c6ffa38",
            measurementId: "G-8JDVNCV8FW"
        };
        
        const appId = firebaseConfig.projectId;

        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);
        const auth = getAuth(app);
        
        // Firebase Auth
        async function signIn() {
            try {
                if (typeof __initial_auth_token !== 'undefined') {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }
                console.log("Firebase signed in successfully.");
                // Start listeners after successful login
                initAdmin();
            } catch (error) {
                console.error("Firebase sign in failed:", error);
            }
        }
        signIn();

        // UI elements
        const passwordInput = document.getElementById('passwordInput');
        const loginButton = document.getElementById('loginButton');
        const passwordSection = document.getElementById('passwordSection');
        const adminContent = document.getElementById('adminContent');
        const loginMessage = document.getElementById('loginMessage');
        const addPasswordInput = document.getElementById('addPasswordInput');
        const resetPasswordInput = document.getElementById('resetPasswordInput');

        const ADMIN_PASSWORD = "tiian";
        
        loginButton.addEventListener('click', () => {
            if (passwordInput.value === ADMIN_PASSWORD) {
                passwordSection.style.display = 'none';
                adminContent.style.display = 'block';
                showAdminMessage('Selamat datang, Admin!', false);
                addPasswordInput.value = ADMIN_PASSWORD;
                resetPasswordInput.value = ADMIN_PASSWORD;
            } else {
                showAdminMessage('Password salah. Silakan coba lagi.', true);
                passwordInput.value = '';
            }
        });

        const tabButtons = document.querySelectorAll('.tab-button');
        const tabContents = document.querySelectorAll('.tab-content');

        const participantsList = document.getElementById('participantsList');
        const resetParticipantsButton = document.getElementById('resetParticipantsButton');
        const addParticipantForm = document.getElementById('addParticipantForm');

        const prizeNameInput = document.getElementById('prizeName');
        const prizeImageInput = document.getElementById('prizeImage');
        const prizeQuotaInput = document.getElementById('prizeQuota');
        const addPrizeButton = document.getElementById('addPrizeButton');
        const regularPrizesList = document.getElementById('regularPrizesList');

        const grandPrizeNameInput = document.getElementById('grandPrizeName');
        const grandPrizeImageInput = document.getElementById('grandPrizeImage');
        const grandPrizeRankInput = document.getElementById('grandPrizeRank');
        const addGrandPrizeButton = document.getElementById('addGrandPrizeButton');
        const grandPrizesList = document.getElementById('grandPrizesList');
        
        const regularWinnersList = document.getElementById('regularWinnersList');
        const grandWinnersList = document.getElementById('grandWinnersList');

        const deleteWinnerModal = document.getElementById('deleteWinnerModal');
        const confirmDeleteButton = document.getElementById('confirmDeleteButton');
        const cancelDeleteButton = document.getElementById('cancelDeleteButton');

        let winnerToDelete = null;

        function showAdminMessage(message, isError = false) {
            const el = document.getElementById('adminMessage');
            el.textContent = message;
            el.classList.toggle('error', isError);
            el.style.display = 'block';
            setTimeout(() => {
                el.style.display = 'none';
            }, 3000);
        }

        function switchTab(tabId) {
            tabContents.forEach(content => {
                content.classList.remove('active');
            });
            tabButtons.forEach(button => {
                button.classList.remove('active');
            });

            document.getElementById(tabId + '-tab').classList.add('active');
            document.querySelector(`.tab-button[data-tab='${tabId}']`).classList.add('active');
        }

        tabButtons.forEach(button => {
            button.addEventListener('click', () => {
                const tab = button.getAttribute('data-tab');
                switchTab(tab);
            });
        });
        
        async function fetchParticipants() {
            try {
                const response = await fetch('participants.json');
                const data = await response.json();
                renderParticipants(data.participants || []);
            } catch (error) {
                console.error("Error fetching participants:", error);
                participantsList.innerHTML = '<p style="text-align: center; color: var(--red-error); font-style: italic;">Gagal memuat peserta.</p>';
            }
        }
        
        function renderParticipants(participants) {
            participantsList.innerHTML = '';
            if (participants.length === 0) {
                participantsList.innerHTML = '<p style="text-align: center; color: var(--gray); font-style: italic;">Belum ada peserta.</p>';
                return;
            }
            participants.forEach(p => {
                const item = document.createElement('div');
                item.classList.add('list-item');
                let status = '';
                if (p.hasWon) {
                    status = '(Sudah Menang)';
                } else if (p.isGrandWinner) {
                    status = '(Pemenang Grand Prize)';
                }
                item.innerHTML = `
                    <span>${p.name} ${status}</span>
                    <form onsubmit="handleDelete(event, '${p.id}')">
                        <input type="hidden" name="action" value="delete">
                        <input type="hidden" name="id" value="${p.id}">
                        <input type="hidden" name="password" id="deletePasswordInput_${p.id}" value="${ADMIN_PASSWORD}">
                        <button type="submit" class="button button-danger">Hapus</button>
                    </form>
                `;
                participantsList.appendChild(item);
            });
        }
        
        async function handleDelete(event, id) {
            event.preventDefault();
            const form = event.target;
            const formData = new FormData(form);
            try {
                const response = await fetch('admin.php', {
                    method: 'POST',
                    body: formData
                });
                const result = await response.json();
                if (result.success) {
                    showAdminMessage(result.message);
                    fetchParticipants();
                } else {
                    showAdminMessage(result.message, true);
                }
            } catch (error) {
                console.error('Error:', error);
                showAdminMessage('Gagal menghapus peserta.', true);
            }
        }
        
        addParticipantForm.addEventListener('submit', async (event) => {
            event.preventDefault();
            const formData = new FormData(addParticipantForm);
            formData.append('action', 'add');
            formData.append('password', ADMIN_PASSWORD);

            try {
                const response = await fetch('admin.php', {
                    method: 'POST',
                    body: formData
                });
                const result = await response.json();
                if (result.success) {
                    showAdminMessage(result.message);
                    document.getElementById('participantNames').value = '';
                    fetchParticipants();
                } else {
                    showAdminMessage(result.message, true);
                }
            } catch (error) {
                console.error('Error:', error);
                showAdminMessage('Gagal menambahkan peserta.', true);
            }
        });

        resetParticipantsButton.addEventListener('click', async () => {
            if (confirm('Anda yakin ingin mereset semua daftar pemenang? Nama-nama yang sudah menang akan kembali ke daftar undian.')) {
                const formData = new FormData();
                formData.append('action', 'reset');
                formData.append('password', ADMIN_PASSWORD);
                try {
                    const response = await fetch('admin.php', {
                        method: 'POST',
                        body: formData
                    });
                    const result = await response.json();
                    if (result.success) {
                        showAdminMessage(result.message);
                        fetchParticipants();
                    } else {
                        showAdminMessage(result.message, true);
                    }
                } catch (error) {
                    console.error('Error:', error);
                    showAdminMessage('Gagal mereset peserta.', true);
                }
            }
        });

        function initAdmin() {
            fetchParticipants();

            // Firestore data paths
            const configDocRef = doc(db, `artifacts/${appId}/public/data/config`, 'drawConfig');
            const winnersColRef = collection(db, `artifacts/${appId}/public/data/winners`);
            const grandWinnersColRef = collection(db, `artifacts/${appId}/public/data/grandWinners`);

            // Listeners for real-time updates
            onSnapshot(winnersColRef, (snapshot) => {
                regularWinnersList.innerHTML = '';
                if (snapshot.empty) {
                    regularWinnersList.innerHTML = '<p style="text-align: center; color: var(--gray); font-style: italic;">Belum ada pemenang undian biasa.</p>';
                    return;
                }
                snapshot.forEach(doc => {
                    const data = doc.data();
                    const item = document.createElement('div');
                    item.classList.add('winner-list-item');
                    item.innerHTML = `
                        <div>
                            <span>${data.name}</span>
                            <div style="font-size: 0.9rem; color: var(--gray);">
                                <span>Hadiah: ${data.prizeName}</span>
                            </div>
                        </div>
                        <button class="button button-danger delete-winner" data-id="${doc.id}" data-type="regular">Hapus</button>
                    `;
                    regularWinnersList.appendChild(item);
                });
            });
            
            onSnapshot(grandWinnersColRef, (snapshot) => {
                grandWinnersList.innerHTML = '';
                if (snapshot.empty) {
                    grandWinnersList.innerHTML = '<p style="text-align: center; color: var(--gray); font-style: italic;">Belum ada pemenang Grand Lucky Draw.</p>';
                    return;
                }
                snapshot.forEach(doc => {
                    const data = doc.data();
                    const item = document.createElement('div');
                    item.classList.add('winner-list-item');
                    item.innerHTML = `
                        <div>
                            <span>${data.name}</span>
                            <div style="font-size: 0.9rem; color: var(--gray);">
                                <span>Hadiah: ${data.prizeName} (${data.prizeRank})</span>
                            </div>
                        </div>
                        <button class="button button-danger delete-winner" data-id="${doc.id}" data-type="grand">Hapus</button>
                    `;
                    grandWinnersList.appendChild(item);
                });
            });

            onSnapshot(configDocRef, (docSnap) => {
                if (docSnap.exists()) {
                    const data = docSnap.data();
                    renderPrizes(data.prizes || [], regularPrizesList, 'regular');
                    renderPrizes(data.grandPrizes || [], grandPrizesList, 'grand');
                }
            });

            function renderPrizes(prizes, listElement, type) {
                listElement.innerHTML = '';
                if (prizes.length === 0) {
                     listElement.innerHTML = '<p style="text-align: center; color: var(--gray); font-style: italic;">Belum ada hadiah.</p>';
                     return;
                }
                prizes.forEach((prize, index) => {
                    const item = document.createElement('div');
                    item.classList.add('list-item');
                    item.innerHTML = `
                        <div class="prize-item">
                            <img src="${prize.image}" onerror="this.src='https://placehold.co/50x50/E0E0E0/4B4B4B?text=Hadiah';" alt="${prize.name}" class="prize-image-preview">
                            <span>${prize.name}</span>
                            ${type === 'regular' ? `<span>(Kuota: ${prize.quota})</span>` : `<span>(Peringkat: ${prize.rank})</span>`}
                        </div>
                        <button class="button button-danger delete-prize" data-index="${index}" data-type="${type}">Hapus</button>
                    `;
                    listElement.appendChild(item);
                });
            }

            regularWinnersList.addEventListener('click', (e) => {
                if (e.target.classList.contains('delete-winner')) {
                    winnerToDelete = {
                        id: e.target.getAttribute('data-id'),
                        type: e.target.getAttribute('data-type')
                    };
                    deleteWinnerModal.style.display = 'flex';
                }
            });
            
            grandWinnersList.addEventListener('click', (e) => {
                if (e.target.classList.contains('delete-winner')) {
                    winnerToDelete = {
                        id: e.target.getAttribute('data-id'),
                        type: e.target.getAttribute('data-type')
                    };
                    deleteWinnerModal.style.display = 'flex';
                }
            });

            confirmDeleteButton.addEventListener('click', async () => {
                if (winnerToDelete) {
                    deleteWinnerModal.style.display = 'none';
                    try {
                        let collectionRef;
                        if (winnerToDelete.type === 'regular') {
                            collectionRef = winnersColRef;
                        } else {
                            collectionRef = grandWinnersColRef;
                        }
                        await deleteDoc(doc(collectionRef, winnerToDelete.id));
                        showAdminMessage('Pemenang berhasil dihapus. Nama akan kembali ke undian.');
                    } catch (e) {
                        console.error("Error deleting winner:", e);
                        showAdminMessage('Gagal menghapus pemenang.', true);
                    } finally {
                        winnerToDelete = null;
                    }
                }
            });

            cancelDeleteButton.addEventListener('click', () => {
                deleteWinnerModal.style.display = 'none';
                winnerToDelete = null;
            });
            
            addPrizeButton.addEventListener('click', async () => {
                const name = prizeNameInput.value.trim();
                const image = prizeImageInput.value.trim();
                const quota = parseInt(prizeQuotaInput.value, 10);
                if (name && image && !isNaN(quota) && quota > 0) {
                    try {
                        const docSnap = await getDoc(configDocRef);
                        const currentPrizes = docSnap.data()?.prizes || [];
                        const newPrize = { name, image, quota, id: crypto.randomUUID() };
                        currentPrizes.push(newPrize);
                        await setDoc(configDocRef, { prizes: currentPrizes }, { merge: true });
                        prizeNameInput.value = '';
                        prizeImageInput.value = '';
                        prizeQuotaInput.value = '';
                        showAdminMessage('Hadiah undian biasa berhasil ditambahkan.');
                    } catch (e) {
                        console.error("Error adding prize: ", e);
                        showAdminMessage('Gagal menambahkan hadiah.', true);
                    }
                } else {
                     showAdminMessage('Pastikan semua input terisi dengan benar (nama, URL gambar, dan kuota > 0).', true);
                }
            });

            regularPrizesList.addEventListener('click', async (e) => {
                if (e.target.classList.contains('delete-prize')) {
                    const index = parseInt(e.target.getAttribute('data-index'), 10);
                    const docSnap = await getDoc(configDocRef);
                    const currentPrizes = docSnap.data()?.prizes || [];
                    currentPrizes.splice(index, 1);
                    await setDoc(configDocRef, { prizes: currentPrizes }, { merge: true });
                    showAdminMessage('Hadiah undian biasa berhasil dihapus.');
                }
            });

            addGrandPrizeButton.addEventListener('click', async () => {
                const name = grandPrizeNameInput.value.trim();
                const image = grandPrizeImageInput.value.trim();
                const rank = parseInt(grandPrizeRankInput.value, 10);
                if (name && image && !isNaN(rank) && rank > 0) {
                    try {
                        const docSnap = await getDoc(configDocRef);
                        const currentPrizes = docSnap.data()?.grandPrizes || [];
                        const newPrize = { name, image, rank, id: crypto.randomUUID() };
                        currentPrizes.push(newPrize);
                        await setDoc(configDocRef, { grandPrizes: currentPrizes }, { merge: true });
                        grandPrizeNameInput.value = '';
                        grandPrizeImageInput.value = '';
                        grandPrizeRankInput.value = '';
                        showAdminMessage('Hadiah grand prize berhasil ditambahkan.');
                    } catch (e) {
                        console.error("Error adding grand prize: ", e);
                        showAdminMessage('Gagal menambahkan grand prize.', true);
                    }
                } else {
                     showAdminMessage('Pastikan semua input terisi dengan benar (nama, URL gambar, dan peringkat > 0).', true);
                }
            });

            grandPrizesList.addEventListener('click', async (e) => {
                if (e.target.classList.contains('delete-prize')) {
                    const index = parseInt(e.target.getAttribute('data-index'), 10);
                    const docSnap = await getDoc(configDocRef);
                    const currentPrizes = docSnap.data()?.grandPrizes || [];
                    currentPrizes.splice(index, 1);
                    await setDoc(configDocRef, { grandPrizes: currentPrizes }, { merge: true });
                    showAdminMessage('Hadiah grand prize berhasil dihapus.');
                }
            });
        }
    </script>
</body>
</html>
