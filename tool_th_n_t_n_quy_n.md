<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tool Thần Tôn Quyền - Tam Quốc Sát</title>

<style>
:root {
    --bg-primary: #1a1625;
    --bg-panel: #262035;
    --bg-card: #322a45;
    --bg-card-hover: #4a3e66;
    --accent-purple: #8b5cf6;
    --accent-purple-hover: #7c3aed;
    --accent-red: #ef4444;
    --accent-red-hover: #dc2626;
    --text-main: #f3f4f6;
    --text-muted: #9ca3af;
    --border-color: #43385d;
    --border-highlight: #6b5299;
}

* {
    box-sizing: border-box;
    user-select: none;
}

body {
    margin: 0;
    background: var(--bg-primary);
    color: var(--text-main);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
    min-height: 100vh;
    line-height: 1.5;
}

header {
    padding: 28px 16px;
    text-align: center;
    background: linear-gradient(180deg, #120e1a 0%, var(--bg-primary) 100%);
    border-bottom: 1px solid var(--border-color);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
}

h1 {
    margin: 0 0 8px;
    font-size: 28px;
    letter-spacing: 1px;
    color: #f3e8ff;
    text-shadow: 0 2px 10px rgba(139, 92, 246, 0.3);
}

.sub {
    color: var(--text-muted);
    font-size: 14px;
}

.wrap {
    max-width: 1000px;
    margin: 0 auto;
    padding: 20px 16px;
}

.panel {
    background: var(--bg-panel);
    border: 1px solid var(--border-color);
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 20px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
}

h2 {
    margin: 0 0 8px;
    font-size: 20px;
    color: #e9d5ff;
    display: flex;
    align-items: center;
    gap: 8px;
}

.note {
    font-size: 13px;
    color: var(--text-muted);
    margin-bottom: 16px;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 12px;
}

.card-btn {
    border: 1px solid var(--border-color);
    background: var(--bg-card);
    color: var(--text-main);
    border-radius: 12px;
    padding: 14px 12px;
    cursor: pointer;
    font-size: 15px;
    font-weight: 500;
    transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
}

.card-btn:hover {
    background: var(--bg-card-hover);
    border-color: var(--border-highlight);
    transform: translateY(-2px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
}

.card-btn:active {
    transform: translateY(0);
}

.card-btn.hidden {
    display: none;
}

.summary {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 10px;
}

.item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #1d1829;
    border: 1px solid var(--border-color);
    border-radius: 10px;
    padding: 10px 14px;
    transition: border-color 0.2s;
}

.item:hover {
    border-color: var(--border-highlight);
}

.item-left {
    display: flex;
    align-items: center;
    gap: 10px;
}

.item-name {
    font-weight: 600;
    color: #f3e8ff;
}

.item-right {
    display: flex;
    align-items: center;
    gap: 8px;
}

.count {
    font-weight: 700;
    font-size: 13px;
    background: var(--accent-purple);
    color: #fff;
    border-radius: 20px;
    padding: 3px 10px;
}

.remove-single {
    background: transparent;
    border: none;
    color: var(--text-muted);
    font-size: 16px;
    cursor: pointer;
    padding: 2px 6px;
    border-radius: 6px;
    transition: all 0.15s;
    line-height: 1;
}

.remove-single:hover {
    color: var(--accent-red);
    background: rgba(239, 68, 68, 0.1);
}

.actions {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin-top: 18px;
    padding-top: 16px;
    border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.action {
    border: 1px solid var(--border-highlight);
    border-radius: 10px;
    background: var(--bg-card);
    color: var(--text-main);
    padding: 10px 16px;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 6px;
}

.action:hover:not(:disabled) {
    background: var(--bg-card-hover);
    transform: translateY(-1px);
}

.action:disabled {
    opacity: 0.4;
    cursor: not-allowed;
    border-color: var(--border-color);
}

.action.reset {
    background: rgba(239, 68, 68, 0.15);
    border-color: rgba(239, 68, 68, 0.4);
    color: #fca5a5;
    margin-left: auto;
}

.action.reset:hover:not(:disabled) {
    background: var(--accent-red);
    color: #fff;
}

.empty {
    color: var(--text-muted);
    padding: 20px 0;
    text-align: center;
    font-style: italic;
    grid-column: 1 / -1;
}

.total {
    text-align: right;
    margin-top: 16px;
    padding-top: 12px;
    border-top: 1px solid var(--border-color);
    color: var(--text-muted);
    font-size: 14px;
}

.total b {
    font-size: 22px;
    color: var(--accent-purple);
    margin-left: 6px;
}

@media (max-width: 600px) {
    header {
        padding: 20px 12px;
    }

    h1 {
        font-size: 22px;
    }

    .wrap {
        padding: 12px;
    }

    .panel {
        padding: 14px;
    }

    .grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 8px;
    }

    .card-btn {
        font-size: 13px;
        padding: 12px 6px;
    }

    .summary {
        grid-template-columns: 1fr;
    }

    .actions {
        flex-direction: column;
    }

    .action.reset {
        margin-left: 0;
    }
}
</style>
</head>

<body>

<header>
    <h1>⚔ TOOL THẦN TÔN QUYỀN ⚔</h1>
    <div class="sub">
        Chọn danh bài → Tự động ẩn lá đã chọn → Hệ thống tự động tổng hợp số lượng
    </div>
</header>

<div class="wrap">

    <!-- ==============================
         KHU VỰC CHỌN BÀI
    =============================== -->
    <div class="panel">
        <h2>🎴 Chọn danh bài</h2>
        <div class="note">
            Nhấp vào tên lá bài bên dưới để ghi nhận. Bài đã chọn sẽ tự động ẩn khỏi danh sách lựa chọn.
        </div>

        <div id="cardGrid" class="grid"></div>

        <div class="actions">
            <button type="button" class="action" id="undoBtn">
                ↩ Hoàn tác lựa chọn cuối
            </button>
            <button type="button" class="action reset" id="resetBtn">
                ↻ Reset chọn lại từ đầu
            </button>
        </div>
    </div>

    <!-- ==============================
         KHU VỰC TỔNG HỢP
    =============================== -->
    <div class="panel">
        <h2>📊 Danh bài đã chọn</h2>
        <div id="summary" class="summary"></div>
        <div id="total" class="total"></div>
    </div>

</div>

<script>
/* =====================================
   DANH SÁCH CÁC LOẠI BÀI
===================================== */
const CARDS = [
    "Sát",
    "Né",
    "Đào",
    "Rượu",
    "Vô Trung Sinh Hữu",
    "Vô Giải Khả Kích",
    "Thuận Thủ Khiên Dương",
    "Quá Hà Sách Kiều",
    "Tá Đao Sát Nhân",
    "Hỏa Công",
    "Quyết Đấu",
    "Nam Man Nhập Xâm",
    "Vạn Tiễn Tề Phát",
    "Đào Viên Kết Nghĩa",
    "Xích Sắt Liên Hoàn"
];

/* =====================================
   DỮ LIỆU ĐÃ CHỌN
===================================== */
let selected = [];

/* =====================================
   ĐỌC DỮ LIỆU TỪ LOCAL STORAGE
===================================== */
try {
    const saved = localStorage.getItem("thanTonQuyen_selected");
    if (saved) {
        const parsed = JSON.parse(saved);
        if (Array.isArray(parsed)) {
            selected = parsed;
        }
    }
} catch (error) {
    console.error("Không thể đọc dữ liệu từ LocalStorage:", error);
    selected = [];
}

/* =====================================
   LƯU DỮ LIỆU
===================================== */
function save() {
    try {
        localStorage.setItem("thanTonQuyen_selected", JSON.stringify(selected));
    } catch (error) {
        console.error("Không thể lưu dữ liệu vào LocalStorage:", error);
    }
}

/* =====================================
   CHỌN BÀI
===================================== */
function choose(card) {
    selected.push(card);
    save();
    render();
}

/* =====================================
   HOÀN TÁC BƯỚC CUỐI
===================================== */
function undoLast() {
    if (selected.length === 0) return;
    selected.pop();
    save();
    render();
}

/* =====================================
   XÓA TOÀN BỘ SỐ LƯỢNG CỦA 1 LOẠI BÀI
===================================== */
function removeCardType(cardName) {
    selected = selected.filter(item => item !== cardName);
    save();
    render();
}

/* =====================================
   RESET TOÀN BỘ
===================================== */
function resetAll() {
    if (selected.length === 0) return;

    const confirmed = confirm("Bạn có chắc chắn muốn xóa toàn bộ danh bài đã chọn không?");
    if (!confirmed) return;

    selected = [];
    save();
    render();
}

/* =====================================
   ĐẾM SỐ LƯỢNG BÀI
===================================== */
function getCounts() {
    const counts = {};
    selected.forEach(card => {
        counts[card] = (counts[card] || 0) + 1;
    });
    return counts;
}

/* =====================================
   HIỂN THỊ CÁC NÚT BÀI
===================================== */
function renderCards(counts) {
    const grid = document.getElementById("cardGrid");
    grid.innerHTML = "";

    CARDS.forEach(card => {
        const button = document.createElement("button");
        button.type = "button";
        button.className = "card-btn";
        button.textContent = card;

        if (counts[card] > 0) {
            button.classList.add("hidden");
        }

        button.addEventListener("click", () => choose(card));
        grid.appendChild(button);
    });
}

/* =====================================
   HIỂN THỊ DANH SÁCH TỔNG HỢP
===================================== */
function renderSummary(counts) {
    const summary = document.getElementById("summary");
    summary.innerHTML = "";

    const entries = Object.entries(counts);

    if (entries.length === 0) {
        const empty = document.createElement("div");
        empty.className = "empty";
        empty.textContent = "Chưa chọn danh bài nào.";
        summary.appendChild(empty);
        return;
    }

    entries.forEach(([name, count]) => {
        const item = document.createElement("div");
        item.className = "item";

        const leftDiv = document.createElement("div");
        leftDiv.className = "item-left";

        const nameElement = document.createElement("span");
        nameElement.className = "item-name";
        nameElement.textContent = name;

        leftDiv.appendChild(nameElement);

        const rightDiv = document.createElement("div");
        rightDiv.className = "item-right";

        const countElement = document.createElement("span");
        countElement.className = "count";
        countElement.textContent = count + " lá";

        const removeBtn = document.createElement("button");
        removeBtn.type = "button";
        removeBtn.className = "remove-single";
        removeBtn.innerHTML = "&#10005;";
        removeBtn.title = "Xóa loại bài này";
        removeBtn.addEventListener("click", () => removeCardType(name));

        rightDiv.appendChild(countElement);
        rightDiv.appendChild(removeBtn);

        item.appendChild(leftDiv);
        item.appendChild(rightDiv);

        summary.appendChild(item);
    });
}

/* =====================================
   HIỂN THỊ TỔNG SỐ LÁ BÀI
===================================== */
function renderTotal() {
    const totalElement = document.getElementById("total");
    const undoBtn = document.getElementById("undoBtn");
    const resetBtn = document.getElementById("resetBtn");
    const total = selected.length;

    if (total === 0) {
        totalElement.innerHTML = "";
        undoBtn.disabled = true;
        resetBtn.disabled = true;
        return;
    }

    undoBtn.disabled = false;
    resetBtn.disabled = false;
    totalElement.innerHTML = "Tổng số bài đã chọn: <b>" + total + "</b> lá";
}

/* =====================================
   RENDER TOÀN BỘ GIAO DIỆN
===================================== */
function render() {
    const counts = getCounts();
    renderCards(counts);
    renderSummary(counts);
    renderTotal();
}

/* =====================================
   GẮN SỰ KIỆN NÚT HỆ THỐNG
===================================== */
document.getElementById("resetBtn").addEventListener("click", resetAll);
document.getElementById("undoBtn").addEventListener("click", undoLast);

/* =====================================
   KHỞI CHẠY ỨNG DỤNG
===================================== */
render();
</script>

</body>
</html>