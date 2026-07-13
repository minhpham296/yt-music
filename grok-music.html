<?php
// index.php
$filename = 'dsbaihat.txt';
$playlist = [];
$success = '';

if (file_exists($filename)) {
    $lines = file($filename, FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);
    $playlist = array_filter(array_map('trim', $lines));
}

// Thêm bài hát
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['add_url'])) {
    $new_url = trim($_POST['add_url']);
    if (!empty($new_url) && (strpos($new_url, 'youtube.com') !== false || strpos($new_url, 'youtu.be') !== false)) {
        // Chuẩn hóa link
        if (strpos($new_url, 'youtu.be') !== false) {
            $id = parse_url($new_url, PHP_URL_PATH);
            $id = ltrim($id, '/');
            $new_url = "https://www.youtube.com/watch?v=" . $id;
        }
        file_put_contents($filename, $new_url . PHP_EOL, FILE_APPEND | LOCK_EX);
        $success = '✅ Đã thêm bài hát thành công!';
    } else {
        $success = '❌ Link không hợp lệ. Vui lòng dùng link YouTube.';
    }
    header("Location: " . $_SERVER['PHP_SELF'] . "?success=1");
    exit;
}

// Xóa bài
if (isset($_GET['delete'])) {
    $index = (int)$_GET['delete'];
    if (isset($playlist[$index])) {
        unset($playlist[$index]);
        file_put_contents($filename, implode(PHP_EOL, $playlist) . PHP_EOL);
    }
    header("Location: " . $_SERVER['PHP_SELF']);
    exit;
}

function get_youtube_id($url) {
    preg_match('/(?:v=|youtu\.be\/|embed\/)([^&\n?#]+)/', $url, $matches);
    return $matches[1] ?? '';
}

function get_youtube_title($url) {
    $id = get_youtube_id($url);
    if (empty($id)) return 'Không xác định';
    $oembed = "https://www.youtube.com/oembed?url=" . urlencode($url) . "&format=json";
    $data = @json_decode(@file_get_contents($oembed), true);
    return $data['title'] ?? 'YouTube Video';
}
?>

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube Playlist</title>
    <style>
        body { font-family: Arial, sans-serif; background:#0f0f0f; color:#fff; margin:0; padding:0; }
        .container { padding: 15px; max-width: 100%; }
        .player { position:relative; padding-top:56.25%; background:#000; margin:15px 0; border-radius:8px; overflow:hidden; }
        .player iframe { position:absolute; top:0; left:0; width:100%; height:100%; }
        form { display:flex; gap:8px; margin:15px 0; }
        input[type=text] { flex:1; padding:14px; border:none; border-radius:6px; background:#333; color:white; font-size:16px; }
        button { padding:14px 20px; background:#ff0000; color:white; border:none; border-radius:6px; }
        .list li { background:#1f1f1f; margin:8px 0; padding:12px; border-radius:8px; display:flex; align-items:center; }
        .list a { flex:1; color:#fff; text-decoration:none; }
        .delete { color:#ff4444; text-decoration:none; padding:6px 12px; background:#333; border-radius:4px; }
    </style>
</head>
<body>
<div class="container">
    <h1 style="text-align:center;">🎵 YouTube Playlist</h1>

    <?php if (!empty($success) || isset($_GET['success'])): ?>
        <p style="background:#004d00; padding:10px; border-radius:6px;"><?= $success ?? '✅ Đã thêm!' ?></p>
    <?php endif; ?>

    <!-- Player -->
    <?php 
    $play_index = isset($_GET['play']) ? (int)$_GET['play'] : 0;
    $current_url = $playlist[$play_index] ?? ($playlist[0] ?? '');
    $vid = get_youtube_id($current_url);
    if ($vid): 
    ?>
        <div class="player">
            <iframe src="https://www.youtube-nocookie.com/embed/<?= htmlspecialchars($vid) ?>?autoplay=1&rel=0" 
                    frameborder="0" allowfullscreen allow="autoplay"></iframe>
        </div>
    <?php endif; ?>

    <!-- Form thêm -->
    <form method="POST" action="">
        <input type="text" name="add_url" placeholder="Dán link YouTube vào đây..." required>
        <button type="submit">➕ Thêm</button>
    </form>

    <h3>Danh sách bài hát (<?= count($playlist) ?>)</h3>
    <ul class="list">
        <?php foreach ($playlist as $i => $url): ?>
            <li>
                <a href="?play=<?= $i ?>">
                    <?= get_youtube_title($url) ?>
                </a>
                <a href="?delete=<?= $i ?>" class="delete" onclick="return confirm('Xóa bài này?')">Xóa</a>
            </li>
        <?php endforeach; ?>
    </ul>

    <p style="text-align:center; color:#888; margin-top:30px; font-size:14px;">
        💡 Mẹo: Trên Safari iPhone → Nhấn <b>aA</b> → Request Desktop Website
    </p>
</div>
</body>
</html>
